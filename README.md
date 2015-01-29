# json-schema-benchmark
Benchmarks for Node.js JSON-schema validators.

Also test against official JSON-schema test suite and check
for validation causing side-effects on schema or data.

# Results

![performance](https://chart.googleapis.com/chart?chxt=x,y&cht=bhs&chco=76A4FB&chls=2.0&chbh=53,4,1&chs=600x419&chxl=-1:|is-my-json-valid|themis|jsck|z-schema 3|jjv|skeemas|jayschema&chd=t2:100,19,10.4,6.7,5.8,1.1,0.1)

|Validator|Relative speed|Number of test runs per second|
|---------|--------------|------------------------------|
|`is-my-json-valid`|100%|6849|
|`themis`|19%|1301|
|`jsck`|10.4%|714|
|`z-schema 3`|6.7%|457|
|`jjv`|5.8%|397|
|`skeemas`|1.1%|78|
|`jayschema`|0.1%|6|

Validators tested: `is-my-json-valid`, `themis`, `z-schema 3`, `jjv`, `skeemas`, `jayschema`, `jsck`, `jassi`, `JSV`, `request-validator`, `json-model`, `tv4`, `jsonschema`, 
(those not in the results above where excluded because of failing tests - see below for details)

`is-my-json-valid` is currently by far the fastest JSON-schema validator out there.

The fastest validator has 100%, the rest a lower score relative to the fastest.
If a validator has a score of 5% that means that it's speed is 5% of the fastest,
meaning that it's 20 times slower than the fastest

The number in parenthesis is the number of validations of the entire test suite per second.

# What is this for?

This test suite uses the official JSON-schema test suite, but it uses it to test the speed of validators.

This also means, that if a validator does not pass a chosen subset of the official test suite, it will show up in these results (below).

This benchmark is using  the `benchmark` module to gain statistically significant results.

Feel free to add more validators to the test suite in a pull request.

# Test failure summary

Number of failed tests per validator (lower is better)

![failing tests](https://chart.googleapis.com/chart?chxt=x,y&cht=bhs&chco=76A4FB&chls=2.0&chbh=26,4,1&chs=600x410&chxl=-1:|is-my-json-valid|jjv|jayschema|z-schema 3|skeemas|themis|jsonschema|jsck|tv4|jassi|json-model|JSV|request-validator&chd=t2:9,9,10,11,13,13,17,21,26,31,40,54,139&chxr=0,0,139)

|Validator|Number of failing tests|
|---------|-----------------------|
|`is-my-json-valid`|9|
|`jjv`|9|
|`jayschema`|10|
|`z-schema 3`|11|
|`skeemas`|13|
|`themis`|13|
|`jsonschema`|17|
|`jsck`|21|
|`tv4`|26|
|`jassi`|31|
|`json-model`|40|
|`JSV`|54|
|`request-validator`|139|

# Side-effects summary

Number of tests that caused side-effects. The schema or data was altered by the validator.

|Validator|Number of side-effects (BAD)|
|---------|----------------------------|
|`tv4`|2|
|`jsonschema`|4|
|`request-validator`|149|
|`json-model`|283|
|`z-schema 3`|290|

Validators not in the list have no side-effects on data or schemas.

# Detailed list of failed tests

## All validators fail these tests (not included under each validator)

remote ref, remote ref invalid

fragment within remote ref, remote fragment invalid

ref within remote ref, ref within ref invalid

change resolution scope, changed scope ref invalid

remote ref, remote ref valid

fragment within remote ref, remote fragment valid

ref within remote ref, ref within ref valid

change resolution scope, changed scope ref valid


## `is-my-json-valid` failed tests

is-my-json-valid failed the test &quot;invalid definition, invalid definition schema&quot;. Expected result: false but validator returned: true

is-my-json-valid failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

is-my-json-valid failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

is-my-json-valid failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

is-my-json-valid failed the test &quot;remote ref, containing refs itself, remote ref invalid&quot;. Expected result: false but validator returned: true

**All other tests passed**.


## `themis` failed tests

themis failed the test &quot;valid definition, valid definition schema&quot;. Expected result: true but validator returned: &quot;Object #&lt;Object&gt; has no method &#39;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&#39;&quot;

themis failed the test &quot;invalid definition, invalid definition schema&quot;. Expected result: false but validator returned: &quot;Object #&lt;Object&gt; has no method &#39;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&#39;&quot;

themis failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

themis failed the test &quot;remote ref, containing refs itself, remote ref valid&quot;. Expected result: true but validator returned: &quot;Object #&lt;Object&gt; has no method &#39;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&#39;&quot;

themis failed the test &quot;remote ref, containing refs itself, remote ref invalid&quot;. Expected result: false but validator returned: &quot;Object #&lt;Object&gt; has no method &#39;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&#39;&quot;

**All other tests passed**.


## `z-schema 3` failed tests

z-schema 3 failed the test &quot;valid definition, valid definition schema&quot;. Expected result: true but validator returned: false

z-schema 3 failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

z-schema 3 failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

z-schema 3 failed the test &quot;validation of URIs, an invalid URI&quot;. Expected result: false but validator returned: true

z-schema 3 failed the test &quot;validation of URIs, an invalid URI though valid URI reference&quot;. Expected result: false but validator returned: true

z-schema 3 failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

z-schema 3 failed the test &quot;remote ref, containing refs itself, remote ref valid&quot;. Expected result: true but validator returned: false

**All other tests passed**.


## `jjv` failed tests

jjv failed the test &quot;valid definition, valid definition schema&quot;. Expected result: true but validator returned: false

jjv failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

jjv failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

jjv failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

jjv failed the test &quot;remote ref, containing refs itself, remote ref valid&quot;. Expected result: true but validator returned: false

**All other tests passed**.


## `skeemas` failed tests

skeemas failed the test &quot;valid definition, valid definition schema&quot;. Expected result: true but validator returned: &quot;Unable to locate JSON Ref (http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema)&quot;

skeemas failed the test &quot;invalid definition, invalid definition schema&quot;. Expected result: false but validator returned: &quot;Unable to locate JSON Ref (http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema)&quot;

skeemas failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

skeemas failed the test &quot;remote ref, containing refs itself, remote ref valid&quot;. Expected result: true but validator returned: &quot;Unable to locate JSON Ref (http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema)&quot;

skeemas failed the test &quot;remote ref, containing refs itself, remote ref invalid&quot;. Expected result: false but validator returned: &quot;Unable to locate JSON Ref (http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema)&quot;

**All other tests passed**.


## `jayschema` failed tests

jayschema failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

jayschema failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

jayschema failed the test &quot;validation of URIs, an invalid URI though valid URI reference&quot;. Expected result: false but validator returned: true

jayschema failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

**All other tests passed**.


## `jsck` failed tests

jsck failed the test &quot;valid definition, valid definition schema&quot;. Because the schema failed to load(Unresolvable $ref values: [&quot;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&quot;])

jsck failed the test &quot;invalid definition, invalid definition schema&quot;. Because the schema failed to load(Unresolvable $ref values: [&quot;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&quot;])

jsck failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

jsck failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

jsck failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

jsck failed the test &quot;remote ref, containing refs itself, remote ref valid&quot;. Because the schema failed to load(Unresolvable $ref values: [&quot;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&quot;])

jsck failed the test &quot;remote ref, containing refs itself, remote ref invalid&quot;. Because the schema failed to load(Unresolvable $ref values: [&quot;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&quot;])

jsck failed the test &quot;uniqueItems validation, non-unique array of integers is invalid&quot;. Expected result: false but validator returned: true

jsck failed the test &quot;uniqueItems validation, numbers are unique if mathematically unequal&quot;. Expected result: false but validator returned: true

jsck failed the test &quot;uniqueItems validation, non-unique array of objects is invalid&quot;. Expected result: false but validator returned: true

jsck failed the test &quot;uniqueItems validation, non-unique array of nested objects is invalid&quot;. Expected result: false but validator returned: true

jsck failed the test &quot;uniqueItems validation, non-unique array of arrays is invalid&quot;. Expected result: false but validator returned: true

jsck failed the test &quot;uniqueItems validation, non-unique heterogeneous types are invalid&quot;. Expected result: false but validator returned: true

**All other tests passed**.


## `jassi` failed tests

jassi failed the test &quot;invalid definition, invalid definition schema&quot;. Expected result: false but validator returned: true

jassi failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

jassi failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

jassi failed the test &quot;validation of date-time strings, an invalid date-time string&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of date-time strings, only RFC3339 not all of ISO 8601 are valid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of URIs, an invalid URI&quot;. Expected result: false but validator returned: true

jassi failed the test &quot;validation of URIs, an invalid URI though valid URI reference&quot;. Expected result: false but validator returned: true

jassi failed the test &quot;validation of e-mail addresses, an invalid e-mail address&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of IP addresses, an IP address with too many components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of IP addresses, an IP address with out-of-range values&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of IP addresses, an IP address without 4 components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of IP addresses, an IP address as an integer&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of IPv6 addresses, an IPv6 address with out-of-range values&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of IPv6 addresses, an IPv6 address with too many components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of IPv6 addresses, an IPv6 address containing illegal characters&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of host names, a host name starting with an illegal character&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of host names, a host name containing illegal characters&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;validation of host names, a host name with a component too long&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

jassi failed the test &quot;root pointer ref, recursive mismatch&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;relative pointer ref to object, mismatch&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;relative pointer ref to array, mismatch array&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;escaped pointer ref, slash&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;escaped pointer ref, tilda&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;escaped pointer ref, percent&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;nested refs, nested ref invalid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

jassi failed the test &quot;remote ref, containing refs itself, remote ref invalid&quot;. Expected result: false but validator returned: true

**All other tests passed**.


## `JSV` failed tests

JSV failed the test &quot;additionalItems as false without items, items defaults to empty schema so everything is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

JSV failed the test &quot;allOf, mismatch second&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;allOf, mismatch first&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;allOf, wrong type&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;allOf with base schema, valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

JSV failed the test &quot;allOf simple types, mismatch one&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;anyOf, neither anyOf valid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;anyOf with base schema, both anyOf invalid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;valid definition, valid definition schema&quot;. Expected result: true but validator returned: false

JSV failed the test &quot;heterogeneous enum validation, one of the enum is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

JSV failed the test &quot;enums in properties, both properties are valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

JSV failed the test &quot;enums in properties, missing optional property is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

JSV failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

JSV failed the test &quot;maxProperties validation, too long is invalid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

JSV failed the test &quot;minProperties validation, too short is invalid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;by int, int by int fail&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;by number, 35 is not multiple of 1.5&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;by small number, 0.00751 is not multiple of 0.0001&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;not, disallowed&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;not multiple types, mismatch&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;not multiple types, other mismatch&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;not more complex schema, mismatch&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;forbidden property, property present&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;oneOf, both oneOf valid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;oneOf, neither oneOf valid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;oneOf with base schema, both oneOf valid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of date-time strings, an invalid date-time string&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of date-time strings, only RFC3339 not all of ISO 8601 are valid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of URIs, an invalid URI&quot;. Expected result: false but validator returned: true

JSV failed the test &quot;validation of URIs, an invalid URI though valid URI reference&quot;. Expected result: false but validator returned: true

JSV failed the test &quot;validation of e-mail addresses, an invalid e-mail address&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of IP addresses, an IP address with too many components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of IP addresses, an IP address with out-of-range values&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of IP addresses, an IP address without 4 components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of IP addresses, an IP address as an integer&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of IPv6 addresses, an IPv6 address with out-of-range values&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of IPv6 addresses, an IPv6 address with too many components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of IPv6 addresses, an IPv6 address containing illegal characters&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of host names, a host name starting with an illegal character&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of host names, a host name containing illegal characters&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;validation of host names, a host name with a component too long&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

JSV failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

JSV failed the test &quot;nested refs, nested ref valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

JSV failed the test &quot;remote ref, containing refs itself, remote ref valid&quot;. Expected result: true but validator returned: false

JSV failed the test &quot;required validation, present required property is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

JSV failed the test &quot;uniqueItems validation, non-unique array of objects is invalid&quot;. Expected result: false but validator returned: true

JSV failed the test &quot;uniqueItems validation, non-unique array of nested objects is invalid&quot;. Expected result: false but validator returned: true

JSV failed the test &quot;uniqueItems validation, non-unique array of arrays is invalid&quot;. Expected result: false but validator returned: true

JSV failed the test &quot;uniqueItems validation, non-unique heterogeneous types are invalid&quot;. Expected result: false but validator returned: true

**All other tests passed**.


## `request-validator` failed tests

request-validator failed the test &quot;additionalItems as schema, additional items match schema&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;items is schema, no additionalItems, all items match schema&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;array of items with no additionalItems, no additional items present&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalItems as false without items, items defaults to empty schema so everything is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalItems as false without items, ignores non-arrays&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalItems are allowed by default, only the first item is validated&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalProperties being false does not allow other properties, no additional properties is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalProperties being false does not allow other properties, ignores non-objects&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalProperties being false does not allow other properties, patternProperties are not additional properties&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalProperties allows a schema which should validate, no additional properties is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalProperties allows a schema which should validate, an additional valid property is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalProperties can exist by itself, an additional valid property is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;additionalProperties are allowed by default, additional properties are allowed&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;allOf, allOf&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;allOf with base schema, valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;allOf simple types, valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;anyOf, first anyOf valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;anyOf, second anyOf valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;anyOf, both anyOf valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;anyOf with base schema, one anyOf valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;invalid type for default, valid when property is specified&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;invalid type for default, still valid when the invalid default is used&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;invalid string value for default, valid when property is specified&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;invalid string value for default, still valid when the invalid default is used&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;valid definition, valid definition schema&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;dependencies, neither&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;dependencies, nondependant&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;dependencies, with dependency&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;dependencies, ignores non-objects&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple dependencies, neither&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple dependencies, nondependants&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple dependencies, with dependencies&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple dependencies subschema, valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple dependencies subschema, no dependency&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;simple enum validation, one of the enum is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;heterogeneous enum validation, one of the enum is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;enums in properties, both properties are valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;enums in properties, missing optional property is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;a schema given for items, valid items&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;a schema given for items, ignores non-arrays&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;an array of schemas for items, correct types&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxItems validation, shorter is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxItems validation, exact length is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxItems validation, ignores non-arrays&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxLength validation, shorter is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxLength validation, exact length is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxLength validation, ignores non-strings&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;maxProperties validation, shorter is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxProperties validation, exact length is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maxProperties validation, ignores non-objects&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maximum validation, below the maximum is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;maximum validation, ignores non-numbers&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;exclusiveMaximum validation, below the maximum is still valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minItems validation, longer is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minItems validation, exact length is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minItems validation, ignores non-arrays&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minLength validation, longer is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minLength validation, exact length is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minLength validation, ignores non-strings&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minProperties validation, longer is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minProperties validation, exact length is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minProperties validation, ignores non-objects&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minimum validation, above the minimum is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;minimum validation, ignores non-numbers&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;exclusiveMinimum validation, above the minimum is still valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;by int, int by int&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;by int, ignores non-numbers&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;by number, zero is multiple of anything&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;by number, 4.5 is multiple of 1.5&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;by small number, 0.0075 is multiple of 0.0001&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;not, allowed&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;not multiple types, valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;not more complex schema, match&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;not more complex schema, other match&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;forbidden property, property absent&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;oneOf, first oneOf valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;oneOf, second oneOf valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;oneOf with base schema, one oneOf valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;integer, a bignum is an integer&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;number, a bignum is a number&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;integer, a negative bignum is an integer&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;number, a negative bignum is a number&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;integer comparison, comparison works for high numbers&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;integer comparison, comparison works for very negative numbers&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;validation of date-time strings, a valid date-time string&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;validation of URIs, a valid URI&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;validation of e-mail addresses, a valid e-mail address&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;validation of IP addresses, a valid IP address&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;validation of IPv6 addresses, a valid IPv6 address&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;validation of host names, a valid host name&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;pattern validation, a matching pattern is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;pattern validation, ignores non-strings&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;patternProperties validates properties matching a regex, a single valid match is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;patternProperties validates properties matching a regex, multiple valid matches is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;patternProperties validates properties matching a regex, ignores non-objects&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple simultaneous patternProperties are validated, a single valid match is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple simultaneous patternProperties are validated, a simultaneous match is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple simultaneous patternProperties are validated, multiple matches is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;regexes are not anchored by default and are case sensitive, non recognized members are ignored&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;regexes are not anchored by default and are case sensitive, regexes are case sensitive&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;object properties validation, both properties present and valid is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;object properties validation, doesn&#39;t invalidate other properties&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;object properties validation, ignores non-objects&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;properties, patternProperties, additionalProperties interaction, property validates property&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;properties, patternProperties, additionalProperties interaction, patternProperty validates nonproperty&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;properties, patternProperties, additionalProperties interaction, additionalProperty ignores property&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;properties, patternProperties, additionalProperties interaction, additionalProperty validates others&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;root pointer ref, match&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;root pointer ref, recursive match&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;relative pointer ref to object, match&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;relative pointer ref to array, match array&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;nested refs, nested ref valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;remote ref, containing refs itself, remote ref valid&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;required validation, present required property is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;required default validation, not required by default&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;integer type matches integers, an integer is an integer&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;number type matches numbers, an integer is a number&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;number type matches numbers, a float is a number&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;string type matches strings, a string is a string&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;object type matches objects, an object is an object&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;array type matches arrays, an array is not an array&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;boolean type matches booleans, a boolean is not a boolean&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;null type matches only the null object, null is null&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple types can be specified in an array, an integer is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;multiple types can be specified in an array, a string is valid&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

request-validator failed the test &quot;uniqueItems validation, unique array of integers is valid&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;uniqueItems validation, unique array of objects is valid&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;uniqueItems validation, unique array of nested objects is valid&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;uniqueItems validation, unique array of arrays is valid&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;uniqueItems validation, 1 and true are unique&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;uniqueItems validation, 0 and false are unique&quot;. Expected result: true but validator returned: false

request-validator failed the test &quot;uniqueItems validation, unique heterogeneous types are valid&quot;. Expected result: true but validator returned: false

**All other tests passed**.


## `json-model` failed tests

json-model failed the test &quot;valid definition, valid definition schema&quot;. Because the schema failed to load(Requests not enabled - try JsonModel.setRequestFunction(func):
{&quot;method&quot;:&quot;GET&quot;,&quot;url&quot;:&quot;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema&quot;})

json-model failed the test &quot;invalid definition, invalid definition schema&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;simple enum validation, something else is invalid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;heterogeneous enum validation, something else is invalid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;heterogeneous enum validation, objects are deep compared&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;not, disallowed&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;not multiple types, mismatch&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;not multiple types, other mismatch&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;not more complex schema, mismatch&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;forbidden property, property present&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of date-time strings, an invalid date-time string&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of date-time strings, only RFC3339 not all of ISO 8601 are valid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of URIs, an invalid URI&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;validation of URIs, an invalid URI though valid URI reference&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;validation of e-mail addresses, an invalid e-mail address&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of IP addresses, an IP address with too many components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of IP addresses, an IP address with out-of-range values&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of IP addresses, an IP address without 4 components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of IP addresses, an IP address as an integer&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of IPv6 addresses, an IPv6 address with out-of-range values&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of IPv6 addresses, an IPv6 address with too many components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of IPv6 addresses, an IPv6 address containing illegal characters&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of host names, a host name starting with an illegal character&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of host names, a host name containing illegal characters&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;validation of host names, a host name with a component too long&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

json-model failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;remote ref, containing refs itself, remote ref invalid&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;uniqueItems validation, non-unique array of integers is invalid&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;uniqueItems validation, numbers are unique if mathematically unequal&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;uniqueItems validation, non-unique array of objects is invalid&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;uniqueItems validation, non-unique array of nested objects is invalid&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;uniqueItems validation, non-unique array of arrays is invalid&quot;. Expected result: false but validator returned: true

json-model failed the test &quot;uniqueItems validation, non-unique heterogeneous types are invalid&quot;. Expected result: false but validator returned: true

**All other tests passed**.


## `tv4` failed tests

tv4 failed the test &quot;invalid definition, invalid definition schema&quot;. Expected result: false but validator returned: true

tv4 failed the test &quot;heterogeneous enum validation, something else is invalid&quot;. Expected result: false but validator returned: &quot;Cannot read property &#39;foo&#39; of null&quot;. **This excludes this validator from performance tests**

tv4 failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

tv4 failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

tv4 failed the test &quot;validation of date-time strings, an invalid date-time string&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of date-time strings, only RFC3339 not all of ISO 8601 are valid&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of URIs, an invalid URI&quot;. Expected result: false but validator returned: true

tv4 failed the test &quot;validation of URIs, an invalid URI though valid URI reference&quot;. Expected result: false but validator returned: true

tv4 failed the test &quot;validation of e-mail addresses, an invalid e-mail address&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of IP addresses, an IP address with too many components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of IP addresses, an IP address with out-of-range values&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of IP addresses, an IP address without 4 components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of IP addresses, an IP address as an integer&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of IPv6 addresses, an IPv6 address with out-of-range values&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of IPv6 addresses, an IPv6 address with too many components&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of IPv6 addresses, an IPv6 address containing illegal characters&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of host names, a host name starting with an illegal character&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of host names, a host name containing illegal characters&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;validation of host names, a host name with a component too long&quot;. Expected result: false but validator returned: true. **This excludes this validator from performance tests**

tv4 failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

tv4 failed the test &quot;remote ref, containing refs itself, remote ref invalid&quot;. Expected result: false but validator returned: true

tv4 failed the test &quot;uniqueItems validation, unique heterogeneous types are valid&quot;. Expected result: true but validator returned: false

**All other tests passed**.


## `jsonschema` failed tests

jsonschema failed the test &quot;valid definition, valid definition schema&quot;. Expected result: true but validator returned: &quot;no such schema &lt;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&gt;&quot;

jsonschema failed the test &quot;invalid definition, invalid definition schema&quot;. Expected result: false but validator returned: &quot;no such schema &lt;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&gt;&quot;

jsonschema failed the test &quot;maxLength validation, two supplementary Unicode code points is long enough&quot;. Expected result: true but validator returned: false

jsonschema failed the test &quot;minLength validation, one supplementary Unicode code point is not long enough&quot;. Expected result: false but validator returned: true

jsonschema failed the test &quot;validation of date-time strings, a valid date-time string&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

jsonschema failed the test &quot;validation of host names, a valid host name&quot;. Expected result: true but validator returned: false. **This excludes this validator from performance tests**

jsonschema failed the test &quot;some languages do not distinguish between different types of numeric value, a float is not an integer even without fractional part&quot;. Expected result: false but validator returned: true

jsonschema failed the test &quot;remote ref, containing refs itself, remote ref valid&quot;. Expected result: true but validator returned: &quot;no such schema &lt;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&gt;&quot;

jsonschema failed the test &quot;remote ref, containing refs itself, remote ref invalid&quot;. Expected result: false but validator returned: &quot;no such schema &lt;http:&#x2F;&#x2F;json-schema.org&#x2F;draft-04&#x2F;schema#&gt;&quot;

**All other tests passed**.


# Thanks
This code was originally pulled out from the benchmarks in the `themis` json-schema validator.
Thanks goes to Johny Jose for his work.

# License
MIT
