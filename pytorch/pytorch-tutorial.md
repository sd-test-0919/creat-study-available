### QUICKSTART
##### Working with data
- torch.utils.data.Dataset. 
  - Dataset stores the samples and their corresponding label
  - PyTorch offers domain-specific libraries such as TorchText, TorchVision, and TorchAudio
- torch.utils.data.DataLoader 
  - DataLoader wraps an iterable around the Dataset
  - This wraps an iterable over our dataset, and supports automatic batching, sampling, shuffling and multiprocess data loading. 
##### Creating Models
 - create a class 
  - inherits from nn.Module. 
  - __init__ function
  - forward function.
  - accelerate operations 
    - move it to the GPU if available.
    - # Get cpu or gpu device for training.
      device = "cuda" if torch.cuda.is_available() else "cpu"
      print(f"Using {device} device")
      ...
      model = NeuralNetwork().to(device)
      print(model)
