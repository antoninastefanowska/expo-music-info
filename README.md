# expo-music-info
Expo-compatible React Native audio metadata extractor.

Pure JavaScript.
Supports ID3v2.3.0 and ID3v2.4.0 tags (no flags).

## Getting started
```
expo install expo-music-info
```

## Usage
Use this module to retrieve audio metadata from file URI.

```
MusicInfo.getMusicInfoAsync(fileUri, options);
```

Example:
```
import MusicInfo from 'expo-music-info';

let metadata = await MusicInfo.getMusicInfoAsync('file:///storage/emulated/0/Music/far_from_love.mp3', {
  title: true,
  artist: true,
  album: true,
  genre: true,
  picture: true  
});

```

Result:
```
MusicInfo {
  "title": "Far from love",
  "album": "Missquerada",
  "artist": "Missquerada",
  "picture": Object {
    "description": "",
    "pictureData": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAgEASABIAAD...
  }
}
```
If the specified audio file has incorrect/unsupported ID3 tag format, the resulting object will be null.

## Options
Specify the information you are interested in. If the audio file's metadata doesn't include specified info, it will have null value in the resulting object.

| Option  | Type    | Default | Description                                        |
|---------|---------|---------|----------------------------------------------------|
| title   | boolean | true    | Whether to include ```TIT2``` tag frame text data. |
| artist  | boolean | true    | Whether to include ```TPE1``` tag frame text data. |
| album   | boolean | true    | Whether to include ```TALB``` tag frame text data. |
| genre   | boolean | false   | Whether to include ```TCON``` tag frame text data. |
| picture | boolean | false   | Whether to include ```APIC``` tag frame data - cover picture's text description and Base64-encoded image binary data. |
