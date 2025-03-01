## Workers Assets + Vitest

This reproduction illustrates an issue with `@cloudflare/vitest-pool-workers` and Assets, where seemingly `run_worker_first` _always_ happens.

## Steps to reproduce
1. Clone the repo
2. Run `npm ci`
3. Run `npm run test`
4. Observe errors with `/foo.txt` returning `Hello World!` instead of `Foobar`.


## Expected behavior
There is a `public` directory that contains `foo.txt. When running the worker via `npm run dev` and hitting `/foo.txt`, the expected `Foobar` is observed. This should also be the case when running the tests.

## Actual behavior
However, when running the tests, only the Worker runs, and the `public` directory is not served, resulting in the Worker's `Hello World!` response on `/foo.txt`.
