# Infer and Report by type

This assessment is graded by the amount of coverage achieved, in addition to readability and ease-of-change.

The data-flow in the code has several variations:

[![](https://mermaid.ink/img/eyJjb2RlIjoiZ3JhcGggTFJcbiAgICBBKElucHV0IHZhbHVlKSAtLT4gQihMb29rdXAgY29vbGluZy50eXBlKVxuICAgIEIgLS0-IEMoUEFTU0lWRSlcbiAgICBCIC0tPiBEKEhJX0FDVElWRSlcbiAgICBCIC0tPiBFKE1FRF9BQ1RJVkUpXG4gICAgQyAtLT4gRihjbGFzc2lmeSBicmVhY2gtY2hlY2spXG4gICAgRCAtLT4gRlxuICAgIEUgLS0-IEZcbiAgICBGIC0tPiBHKGluZmVyIGJyZWFjaClcbiAgICBHIC0tPiBIKHRvIGNvbnRyb2xsZXIpXG4gICAgRyAtLT4gSSh0byBlbWFpbClcbiAgICBJIC0tPiB8aGlnaHxKKEhpZ2ggbWVzc2FnZSlcbiAgICBJIC0tPiB8bG93fEsoTG93IG1lc3NhZ2UpIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRlZmF1bHQifSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZ3JhcGggTFJcbiAgICBBKElucHV0IHZhbHVlKSAtLT4gQihMb29rdXAgY29vbGluZy50eXBlKVxuICAgIEIgLS0-IEMoUEFTU0lWRSlcbiAgICBCIC0tPiBEKEhJX0FDVElWRSlcbiAgICBCIC0tPiBFKE1FRF9BQ1RJVkUpXG4gICAgQyAtLT4gRihjbGFzc2lmeSBicmVhY2gtY2hlY2spXG4gICAgRCAtLT4gRlxuICAgIEUgLS0-IEZcbiAgICBGIC0tPiBHKGluZmVyIGJyZWFjaClcbiAgICBHIC0tPiBIKHRvIGNvbnRyb2xsZXIpXG4gICAgRyAtLT4gSSh0byBlbWFpbClcbiAgICBJIC0tPiB8aGlnaHxKKEhpZ2ggbWVzc2FnZSlcbiAgICBJIC0tPiB8bG93fEsoTG93IG1lc3NhZ2UpIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRlZmF1bHQifSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)

The code uses switch-case / if-else ladders to implement these variations.

Such structures limit the open-ness of the code,
limiting the possibility of parallel working by multiple developers.
They also require repetitive tests.

Try applying the strategy pattern to make the code more 'open', reducing the amount of tests and repetitions, while increasing the coverage.

## Coverage artifact

Notice the coverage artifact created below your build jobs. This contains details of the coverage on your source code.

![](images/coverage-artifact.png)

## Starting point

Pick a starting point for your assessment.

[C](https://classroom.github.com/a/UhChKJxb)

[C++](https://classroom.github.com/a/cDP7RJH3)

[C#](https://classroom.github.com/a/vTCKD-q4)

[Java](https://classroom.github.com/a/Xu4BAP7B)

[Python](https://classroom.github.com/a/5I1L2gNd)
