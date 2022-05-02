layout: page
title: "Basic codes for a python project"
permalink: /Notes/DL/0/

# This page lists the typically used codes/methods in a python project

1. Top level files : 
    There are two ways to load a Python file: 
    as the top-level script, or as a module. 
    A file is loaded as the top-level script if you execute it directly, 
    for instance by typing python myfile.py on the command line. 
    It is loaded as a module when an import statement is encountered inside some other file. 
    There can only be one top-level script at a time; the top-level script is the Python file you ran to start things off.
    When a module is run as the top-level script, it loses its normal name and its name is instead __main__.
    
2. Defining paths
    Including modules (files with the “. py” extension) in the same directory : 
    '''python
    from module1 import *
    '''
    Including modules from the parent directory 
    '''python
    import sys
    import os
    sys.path.append(os.path.join(sys.path[0], '..'))
    '''
    sys.path[0] is the absolute path to the module without the file name. 
    It works both when the module is and is not the top-level script.
    os.path.join(sys.path[0], '..') will point to the parent path.
    sys.path.append add that parent path to the searching space.
    (from https://stackoverflow.com/questions/14132789/relative-imports-for-the-billionth-time/14132912#14132912)
    
    Here is another way : 
    '''python
    module_path = os.path.abspath(os.path.join('..'))
    if module_path not in sys.path:
        sys.path.append(module_path) #parent path
    module_path = os.path.abspath(os.path.join('../..'))
    if module_path not in sys.path:
        sys.path.append(module_path) #two levels parent path
    '''
    
