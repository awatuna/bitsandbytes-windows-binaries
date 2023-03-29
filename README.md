# bitsandbytes-windows-binaries

bitsandbytes windows binary build with cuda 11.8

# install

download and place libbitsandbytes_cuda118.dll

$USERPROFILE$\anaconda3\envs\textgen\lib\site-packages\bitsandbytes\

In \bitsandbytes\cuda_setup\main.py search for:
	
	if not torch.cuda.is_available(): return 'libsbitsandbytes_cpu.so', None, None, None, None
  
and replace with:

	if torch.cuda.is_available(): return 'libbitsandbytes_cuda118.dll', None, None, None, None
	
In \bitsandbytes\cuda_setup\main.py search for this twice (2 times):

	self.lib = ct.cdll.LoadLibrary(binary_path)
  
and replace with:

	self.lib = ct.cdll.LoadLibrary(str(binary_path))
