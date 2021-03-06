---
title: 'frequencyBinCount'
readiness: 'Ready to Use'
relationships:
  applies_to:
    predicate: 'Property of '
    value: apis/webaudio/AnalyserNode
    href: /apis/webaudio/AnalyserNode
  return:
    predicate: 'Returns an object of type '
    value: 'unsigned long'
    href: /apis/webaudio/AnalyserNode
standardization_status: 'W3C Editor''s Draft'
summary: 'Half the fftSize (the size of the FFT used for frequency-domain analysis).'
tags:
  - API_Object_Properties
  - API
  - WebAudio
uri: apis/webaudio/AnalyserNode/frequencyBinCount

---
## Summary

Half the fftSize (the size of the FFT used for frequency-domain analysis).

Property of [apis/webaudio/AnalyserNode](/apis/webaudio/AnalyserNode)[apis/webaudio/AnalyserNode](/apis/webaudio/AnalyserNode)

## Syntax

``` js
var result = AnalyserNode.frequencyBinCount;
AnalyserNode.frequencyBinCount = value;
```

## Return Value

Returns an object of type unsigned longunsigned long

## Examples

``` js
var audioCtx = new AudioContext();
var analyser = audioCtx.createAnalyser();
var bufferLength = analyser.frequencyBinCount;
```

## Related specifications

[Web Audio API](http://webaudio.github.io/web-audio-api/)
:   W3C Editor's Draft
