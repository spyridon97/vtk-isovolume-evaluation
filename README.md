# VTK Isovolume Evaluation

Repository to evaluate the performance of isovolume filters in VTK

## Build Instructions

There are 2 directories in this repository. One for sequential and one for parallel.

### Sequential

```bash
cd seq
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON -DVTK_SMP_IMPLEMENTATION_TYPE=TBB ..
cmake --build . --target seqIsovolume -j
``` 

### Parallel

```bash
cd par
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON -DVTK_SMP_IMPLEMENTATION_TYPE=TBB ..
cmake --build . --target parIsovolume -j
```

## Datasets

https://drive.google.com/drive/folders/1RfmTb2kLGVUuX2pHDQN9lg2eYAszVdBs

## Execution Instructions

### Sequential

```bash
/usr/bin/time -vv ./seq/build/seqIsovolume inputFile numberOfIterations  
```

### Parallel

```bash
/usr/bin/time -vv ./par/build/parIsovolume inputFile numberOfIterations numberOfThreads  
```
