PROBLEM STATEMENT
The problem statement is that Adobe podcast is an audio rendering software that produces high-quality audio output similar to that of a studio. However, the software currently lacks a feature that automatically removes cuss and abusive words from audio in one click. This feature is available in other non-Adobe products for English language audio (manual work required there), but not in Adobe podcast or other Adobe audio processing software such as Premier Pro and Premier Rush. The proposed solution is to develop a feature that can automatically remove offensive language from audio in one click, for english and other regional languages. The aim is to make Adobe podcast and other Adobe audio processing software more competitive in the market and to promote a more positive and respectful audio environment.
Though this problem seems simple, but there doesn’t exist any such filter which automatically beeps cuss words in audio/video in one click.  

SOLUTION
The possible solutions are:
Convert the audio to text using speech-to-text and then apply our machine learning model to detect the cuss/abusive words based on the threshold score that how much that particular word is inappropriate we should either declare it to be an abusive word or normal word. And then return the timeframe where that word is and then we’ll mute/beep the audio for that particular timeframe. 
First we remove any noise from the audio
Then we convert audio to text using whisper API. 
We are using Whisperx API which gives us word by word sychronised time duration of each word in audio in JSON format.
We then process that json file to check for cuss words for each word. 
One by one we check if that word is cuss/abusive word or not (we are using better_profanity  library).
If it’s a cuss word, then we create a beep sound of same duration and we mute the original audio for that time frame and add beep sound by overlaying for that particular word timeframe. 
At the end we have the audio which contains cuss/abusive word free audio. We can simply export it.


In Above solution, we can use chatGPT API while converting audio to text. It will directly remove the cuss/abusive word while converting, then we don’t need to use any open source library and we will also get better performance. 
By passing audio waveform and then doing similarity search on that waveform for finding cuss/abusive words. 
