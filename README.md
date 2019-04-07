# IDXParser

[![Build Status](https://travis-ci.org/Elzair/IDXParser.jl.svg?branch=master)](https://travis-ci.org/Elzair/IDXParser.jl)

**IDXParser** parses an IDX-formatted file (such as the [MNIST database of handwritten digits](http://yann.lecun.com/exdb/mnist/) and returns an array of values in the given datatype.

## API

Currently, **IDXParser** has only one function:

  * `parseIDX(file_name)` Parses given file

## IDX File Format

| Byte # | Description |
|:------:|:-----------:|
| 0      | 0x00        |
| 1      | 0x00        |
| 2      | Array Datatype: 0x08 -> UInt8, 0x09 -> Int8, 0x0B -> Int16, 0x0C -> Int32, 0x0D -> Float32, 0x0E -> Float64 |
| 3      | # Dimensions: 0x01 for vector, 0x02 for 2D matrix, etc. |
| 4-7    | Length of first dimension (32-bit Little Endian) |
| ...    | ... |
| 4+4n - 4+4n+1 | Start of Data |
