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
    - Get cpu or gpu device for training.  
      device = "cuda" if torch.cuda.is_available() else "cpu"  
      print(f"Using {device} device")  
      ...  
      model = NeuralNetwork().to(device)  
      print(model)  
##### Optimizing the Model Parameters
a loss function and an optimizer.
- makes predictions
- backpropagates the prediction
##### Saving Models
serialize the internal state dictionary
Loading Models
re-creating the model structure and loading the state dictionary 

### TENSORS
encode the inputs and outputs of a model, as well as the model’s parameters.
 NumPy’s ndarrays,tensor可以在gpu上运行
 Initializing a Tensor
 - #Directly from data
 - #From a NumPy array
 - From another tensor:
 - With random or constant values:
 Attributes of a Tensor
- shape, datatype, and the device 
Operations on Tensors
tensors are created on the CPU（default）
# We move our tensor to the GPU if available
if torch.cuda.is_available():
    tensor = tensor.to('cuda')
 - Standard numpy-like indexing and slicing:
 - Joining tensors
  - torch.cat
  - torch.stack：subtly different from torch.cat
 - Arithmetic operations
Bridge with NumPy
A change in the tensor reflects in the NumPy array.
DATASETS & DATALOADERS
### Loading a Dataset
- Iterating and Visualizing the Dataset
  - matplotlib to visualize some samples in our training data.
- Creating a Custom Dataset for your files
  - implement three functions: __init__, __len__, and __getitem__.

















