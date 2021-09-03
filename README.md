# VGGish
A `torch`-compatible port of [VGGish](https://github.com/tensorflow/models/tree/master/research/audioset)<sup>[1]</sup>, 
a feature embedding frontend for audio classification models. The weights are ported directly from the tensorflow model, so embeddings created using `torchvggish` will be identical.
changes from original - instead of resampy this fork used samplerate to resample audio file for use on embedded devices like RPI 4B


## Usage

```python
import torch

model = torch.hub.load('toborobot/torchvggish', 'vggish')
model.eval()

# Download an example audio file
import urllib
url, filename = ("http://soundbible.com/grab.php?id=1698&type=wav", "bus_chatter.wav")
try: urllib.URLopener().retrieve(url, filename)
except: urllib.request.urlretrieve(url, filename)

model.forward(filename)
```

<hr>
[1]  S. Hershey et al., ‘CNN Architectures for Large-Scale Audio Classification’,\
    in International Conference on Acoustics, Speech and Signal Processing (ICASSP),2017\
    Available: https://arxiv.org/abs/1609.09430, https://ai.google/research/pubs/pub45611
    

