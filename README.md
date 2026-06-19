## Introduction
High performance Linq for Unity

Improved performance when using Linq with Mobile (il2cpp).

To use it instead of using `System.Linq` change it to `VirtueSky.Linq`

It will be a little different from `System.Linq` that `Select` is replaced with `Map`, and `Where` is changed to `Filter`


## Benchmark
### Environment:
  - Unity 6000.0.44f1, Build Android IL2CPP
  - Device Redmi Note 10S (Ram 8GB, CPU MediaTek Helio G95 - 2.05GHz, Android 13)
### Setup Test Time:
  - Array size N = 100000 (int)
  - Seed = 42
  - Warmup inters = 3
  - Measure inters = 8
  - Inner loops = 1

| Method                | `System.Linq` <br> Best/Avg (ms) | `VirtueSky.Linq` <br> Best/Avg (ms) |
|-----------------------|----------------------------------|-------------------------------------|
| Aggregate             | 9.106 / 9.313                    | 0.650 / 0.657                       |
| Any                   | 0.012 / 0.012                    | 0.004 / 0.004                       |
| All                   | 9.262 / 9.825                    | 0.650 / 0.665                       |
| Average               | 9.328 / 9.843                    | 0.519 / 0.539                       |
| Contains              | 11.158 / 12.816                  | 1.169 / 1.186                       |
| Count                 | 9.229 / 9.860                    | 0.779 / 0.792                       |
| First                 | 0.011 / 0.012                    | 0.003 / 0.003                       |
| Last                  | 9.968 / 10.025                   | 0.004 / 0.004                       |
| Max                   | 9.169 / 9.842                    | 0.260 / 0.263                       |
| Min                   | 9.161 / 9.842                    | 0.260 / 0.264                       |
| OrderBy -> ToArray    | 48.195 / 49.710                  | 27.805 / 28.505                     |
| Reverse -> ToArray    | 6.021 / 6.343                    | 0.411 / 0.430                       |
| Select -> Sum         | 6.810 / 6.957                    | 1.751 / 1.772                       |
| Skip -> Sum           | 14.256 / 17.235                  | 1.019 / 1.055                       |
| Sum                   | 6.088 / 6.859                    | 0.908 / 0.931                       |
| Take -> Sum           | 0.056 / 0.057                    | 0.009 / 0.010                       |
| Where -> Count        | 3.491 / 3.964                    | 1.934 / 1.972                       |
| Where + Aggregate     | 5.211 / 5.901                    | 1.254 / 1.794                       |
| Where + Select -> Sum | 5.436 / 6.154                    | 1.693 / 1.926                       |
| Where -> Sum          | 4.458 / 6.312                    | 1.815 / 2.011                       |



### Build development check profiler (Test GC)

- Process benchmark `System.Linq`


https://github.com/user-attachments/assets/316766d7-db88-4808-9e7a-86476eb31c64


- Process benchmark `VirtueSky.Linq`



https://github.com/user-attachments/assets/d740b441-d49d-45df-9f7f-3f9e45cc0021


==> It seems that `System.Linq` generates more GC than `VirtueSky.Linq`

[Project Benchmark Here](https://github.com/VirtueSky/Benchmark)
