# img_diff

[![Linux/OSX Build Status](https://travis-ci.org/Mike-Neto/img_diff.svg?branch=master)](https://travis-ci.org/Mike-Neto/img_diff)
[![Windows Build Status](https://ci.appveyor.com/api/projects/status/afjuww52fyb2bd3g?svg=true)](https://ci.appveyor.com/project/Mike-Neto/img-diff)
[![Current Version](https://img.shields.io/crates/v/img_diff.svg)](https://crates.io/crates/img_diff)
[![License: MIT](https://img.shields.io/crates/l/img_diff.svg)](#license)

Rust based Command line tool to diff images in 2 structurally similar folders and output diff images.

Comparison is done using [the SSIM algorithm](https://ece.uwaterloo.ca/~z70wang/research/ssim/) at multiple weighed resolutions and relies on the [dssim](https://crates.io/crates/dssim) crate for the comparisons of png images.

BMP files are compared using a by pixel sample algorithm and the output is the MOD of the diffrence between each of the
pixel components (rgb)

The value returned is 1/SSIM-1, where 0 means identical image, and >0 (unbounded) is amount of difference for PNG.

The value returned for bmp images 0 if images are equal and a positive number that scales with the amout of diffrences.

## Future Features

* Support multiple format's of images (JPEG).
* Allow for a threshold to output diff file.
* Provide a single unit of diffrence.

## Usage

    img_diff -s path\to\images -d path\to\images\to\compare -f path\to\output\diff\images

Will go trough all the files in the -s dir and subdir's and compare them to the ones in the -d outputing diff files if a difrence is found to -f dir.

## Compile from source
     git clone https://github.com/Mike-Neto/img_diff.git
     cd img_diff
     cargo build --release

## Test
	cargo test

## Docs
     cargo doc --open

## Crate
[Crates.io](https://crates.io/crates/img_diff)

## Build or Download

You need [Rust](https://www.rust-lang.org/en-US/install.html)

    cargo install img_diff

## License

Copyright 2018 Miguel Mendes

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.