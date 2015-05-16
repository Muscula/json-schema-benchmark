# [`themis`](https://github.com/playlyfe/themis) - test summary

# All validators fail this test

`some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part`

# [`themis`](https://github.com/playlyfe/themis) failed tests

Some validators have deliberately chosen not to support parts of the spec. Go to the [`themis`](https://github.com/playlyfe/themis) homepage to learn if
that is the case for these tests.

|test failed|reason
|-----------|------
|`valid definition, valid definition schema`|Expected result: `true` but validator returned: `"undefined is not a function"`
|`invalid definition, invalid definition schema`|Expected result: `false` but validator returned: `"undefined is not a function"`
|`remote ref, containing refs itself, remote ref valid`|Expected result: `true` but validator returned: `"undefined is not a function"`
|`remote ref, containing refs itself, remote ref invalid`|Expected result: `false` but validator returned: `"undefined is not a function"`
|`remote ref, remote ref valid`|Expected result: `true` but validator returned: `"undefined is not a function"`
|`remote ref, remote ref invalid`|Expected result: `false` but validator returned: `"undefined is not a function"`
|`fragment within remote ref, remote fragment valid`|Expected result: `true` but validator returned: `"undefined is not a function"`
|`fragment within remote ref, remote fragment invalid`|Expected result: `false` but validator returned: `"undefined is not a function"`
|`ref within remote ref, ref within ref valid`|Expected result: `true` but validator returned: `"undefined is not a function"`
|`ref within remote ref, ref within ref invalid`|Expected result: `false` but validator returned: `"undefined is not a function"`
|`change resolution scope, changed scope ref valid`|The schema failed to load(`invalid ref: folderInteger.json in folder/`)
|`change resolution scope, changed scope ref invalid`|The schema failed to load(`invalid ref: folderInteger.json in folder/`)

**All other tests passed**.

[back to benchmarks](https://github.com/Muscula/json-schema-benchmark)