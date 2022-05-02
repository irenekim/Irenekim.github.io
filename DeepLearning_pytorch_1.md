layout: page
title: "basic codes of Deep Learning in pytorch"
permalink: /notes/dl/1/


# Usually in a pytorch deep learning code, there is a model file/folder and a run/train file. There could still be other files such as utils etc.
# This page lists the typically used codes in a run/train file 

1. Defining the device for training : 
    '''
    device = 'cpu' 
    '''
    or 
    '''
    device = 'cuda'
    '''
    
    following is typically used
    '''
    device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
    print('Using device:', device)
    '''
    
    Could use additional Info when using cuda
    '''
    if device.type == 'cuda':
      print(torch.cuda.get_device_name(0))
      print('Memory Usage:')
      print('Allocated:', round(torch.cuda.memory_allocated(0)/1024**3,1), 'GB'))
      print('Cached:   ', round(torch.cuda.memory_reserved(0)/1024**3,1), 'GB'))
    '''
2. Seed for reproducibility:

    There are many kinds of seeds that can be used. Here for a complete reproducibility, I often use : 
    '''
    torch.backends.cudnn.deterministic = True #only applies to CUDA convolution operations : use only deterministic algorithms
    random.seed(args.seed) #this is for custom operators 
    np.random.seed(args.seed) #numpy random number generator
    torch.manual_seed(args.seed) #pytorch : seed the random number generator both for cuda and cpu
    torch.cuda.manual_seed_all(args.seed) #random generation on gpu
    '''
    
