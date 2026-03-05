+++
date = '2026-03-05T20:16:52+03:00'
draft = false
title = 'Encode Less Video Editing'
+++

If you have been on the internet, you've surely encountered some internet memes. A simple search on Startpage shows the noun definition as "An image, video, piece of text, etc., typically humorous in nature, that is copied and spread rapidly by internet users, often with slight variations." If you have been on the internet a bit more, you've surely encountered memes where they got reposted so many times that they are barely legible and in poor quality. Have you ever thought what causes this?

It's simple, **encoding**. Another small internet search defines **encoding** as "The process of converting data from one format to another, typically for storage, transmission, or compression." As media gets encoded more and more, it reduces in quality, allowing you to count the pixels with much more accuracy.

We have a lot of media formats, from the ones we've heard like **.mp4**, **.mkv**, **.mov** to the ones you've probably not encountered before like **ProRes** and **DNxHR**. When we talk about a format, such as .mp4 or .mkv we are actually not talking about a video, or a audio track, we are talking about (often) the both. This is because when we have video, we very often have audio next to it.

## Formats vs. Containers

Remember **.mp3**? It is one of the very popular and widely supported music formats for storing audio, it is also an **encoding format**. **.mp4** on the other hand, **is not a encoding format**. How come? It's because when we store video we have to store both audio and video in a single file. An .mp3 file can only store a single audio track, so when we invented .mp4 we did not invent it as a format but as a **container**. The **container** takes in a video stream and an audio stream, this can even be .mp3, and gives it to the video player on demand.

Then what do we encode the video in? We surely need something like .mp3 for video too, because .mp4 is not a encoding format, how will we encode the video with? The answer is often **H.264**.

**H.264** is currently one of the most popular video encoding formats out there. It takes in a raw video stream, puts **keyframes** in and calculates the differences between the key frames mathematically. This means instead of storing 30 image files and playing them really fast, in the process wasting space by duplicating the existing details up to 30 times, we can just keep the difference between the **keyframes** and save space.

## Why Do We Encode Anyway?

Why do we even encode things? It's to save space. When we record something like a professional movie, we often use special encoders like **ProRes**. We sometimes don't use encoders at all, and save things as **RAW**! This is so our camera doesn't have to think about calculating the differences between keyframes and can just dump whatever it sees to its storage. One downside of this is the filesizes are huge! While you can get by with around 3-4gb of storage for an hour of video in **H.264**, the same video file can be sized upwards of 100-150gb in **RAW**. That's almost the size of a game! 

Another downside of encoding is that when you want to edit something, it becomes slower. Imagine you have to skip around your 1 hour recording constantly to edit things, and every time you land in a frame that is not a **keyframe**, your computer has to calculate the difference up to the frame you are in. If you use **ProRes** for example, since it saves all frames as they are, you don't need to do any kind of computing at all, your only limitation is a fast disk drive.

This is why we categorize our encoders, stuff such as **ProRes**, **DNxHR** are considered **editing codecs**. **H.264**, **x265**, **AV1** and a few others are considered **finalizing codecs**, meaning if you encode your content in one of them you want the best compression ever and don't ever plan to edit it once again.

## The Finalizing Problems

But what if we need to edit something we encoded in a **finalizing encoder** such as **AV1**? Most of our video editors, if supporting AV1, usually won't complain. Your editing speeds will be very slow but you can always turn the AV1 back to **ProRes**. But when you turn the ProRes back into AV1 something magical happens, the algorithm for AV1 is designed to be a finalizing encoder, this means it will try and give you the smallest filesize possible, even if it means getting rid of minor differences between some frames.

If you keep encoding a video on one of the **finalizing encoders** such as AV1, you will end up losing some minor details each pass, but the minor details slowly creep up and become major, noticeable quality loss. This is the same for those memes you see online, each upload to a social media app encodes the video, then someone else downloads it, uploads it again and it gets encoded again and again.

There exists **lossless encoders**, such as **FLAC** and some **editing encoders** (most editing codecs do still compress, but so little it's indistinguishable by human eyes even if you encode between them multiple times), because they are not trying to compress media, they are just pre-calculating (literally marking all frames as **key frames**) the frames between the keyframes so your editing application can easily seek between frames without having to calculate the frame you just landed on from a keyframe 30 frames ago.

But what if we want to work on a finalizing encoder encoded video file without losing quality? Depending on the task you want to do, it is very much possible to edit a video **without encoding it once again**, saving you time spent on encoding and not losing any quality at all.

## How to Edit Without Encoding

Basic video operations, such as cutting a part out, merging two parts can be done through cutting between **keyframes**. Since a video player only requires some keyframes, some **inter-frames** (this is what we call the mathematically calculated difference, as they are not real frames) and some metadata, if we just cut between two keyframes, update some metadata and put it inside of a **container**, the video player will happily play it for us.

The same is true for switching between containers. Want to switch from **.mkv** to **.mp4**? You can take your video stream, audio stream and put it inside of a **.mp4** with **no encoding at all**! It will have no difference than the .mkv as long as we were able to fit the contents in the .mp4 container (it has some weird limitations like not being able to take in OPUS audio, why?????)

This means you can go between **.mkv** and **.mp4** all you want with no quality loss at all. The **container** of the video does not matter.

There are some tools out there for lossless container switching and video editing, I often use **Avidemux**, **lossless-cut** is another great alternative. You can also always use some **ffmpeg** commands. Just put your video in, skip between keyframes, put a start and end to your selection, then on your options, select both audio and video as copy (copy means no encode will happen, the editor will directly copy the frame data out of the video stream), select your preferred **container** (as we have talked, it does not matter at all as long as your players are happy and your container can accept your encoded stream)

You can just put two clips of a video next to each other, using **Avidemux**, just open a file, then open a second file but instead of using the open prompt, use the **append** option. If you need to put a stream to another container that does not support your audio or video encoder, like a popular case with .mp4 is it doesn't support OPUS audio from .mkv containers, you can switch audio from copy to **AAC** or whatever you like, and **only encode the audio**, saving you time and quality on your video stream as it doesn't need to get encoded just because of your audio.
