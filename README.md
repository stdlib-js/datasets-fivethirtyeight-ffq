<!--

@license Apache-2.0

Copyright (c) 2019 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# FiveThirtyEight Food Frequency Questionnaire

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> [_FiveThirtyEight_][fivethirtyeight-nutrition-studies] reader responses to a food frequency questionnaire ([FFQ][ffq]).



<section class="usage">

## Usage

```javascript
import dataset from 'https://cdn.jsdelivr.net/gh/stdlib-js/datasets-fivethirtyeight-ffq@esm/index.mjs';
```

#### dataset()

Returns [_FiveThirtyEight_][fivethirtyeight-nutrition-studies] reader responses to a food frequency questionnaire ([FFQ][ffq]).

```javascript
var data = dataset();
// returns [ {...}, ... ]
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   The administered food frequency questionnaire ([FFQ][ffq]) was the proprietary [Block FFQ][block-ffq].

</section>

<!-- /.examples -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

import bifurcateBy from 'https://cdn.jsdelivr.net/gh/stdlib-js/utils-bifurcate-by@esm/index.mjs';
import inmap from 'https://cdn.jsdelivr.net/gh/stdlib-js/utils-inmap@esm/index.mjs';
import ttest2 from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-ttest2@esm/index.mjs';
import dataset from 'https://cdn.jsdelivr.net/gh/stdlib-js/datasets-fivethirtyeight-ffq@esm/index.mjs';

function predicate( v ) {
    return ( v.diabetes === 1 );
}

function createAccessor( field ) {
    return accessor;

    function accessor( v ) {
        return v[ field ];
    }
}

// Retrieve the data:
var data = dataset();

// Split the data into two groups based on whether a respondent has diabetes:
var groups = bifurcateBy( data, predicate );

// For each group, extract the frequency of green salad consumption:
var mapFcn = createAccessor( 'greensaladfreq' );
var g1 = inmap( groups[ 0 ].slice(), mapFcn );
var g2 = inmap( groups[ 1 ].slice(), mapFcn );

// Perform a two-sample two-sided Student's t-test to determine if green salad consumption is different between the two groups:
var results = ttest2( g1, g2 );
console.log( results.print() );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->



* * *

<section class="references">

## References

-   Aschwanden, Christie. 2016. "You Can't Trust What You Read About Nutrition." <https://fivethirtyeight.com/features/you-cant-trust-what-you-read-about-nutrition/>.

</section>

<!-- /.references -->

<!-- <license> -->

## License

The data files (databases) are licensed under an [Open Data Commons Attribution 1.0 License][odc-by-1.0] and their contents are licensed under a [Creative Commons Attribution 4.0 International Public License][cc-by-4.0]. The original dataset is attributed to _FiveThirtyEight_ and can be found [here][fivethirtyeight-nutrition-studies]. The software is licensed under [Apache License, Version 2.0][apache-license].

<!-- </license> -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## Copyright

Copyright &copy; 2016-2023. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/datasets-fivethirtyeight-ffq.svg
[npm-url]: https://npmjs.org/package/@stdlib/datasets-fivethirtyeight-ffq

[test-image]: https://github.com/stdlib-js/datasets-fivethirtyeight-ffq/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/datasets-fivethirtyeight-ffq/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/datasets-fivethirtyeight-ffq/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/datasets-fivethirtyeight-ffq?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/datasets-fivethirtyeight-ffq.svg
[dependencies-url]: https://david-dm.org/stdlib-js/datasets-fivethirtyeight-ffq/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/datasets-fivethirtyeight-ffq/tree/deno
[umd-url]: https://github.com/stdlib-js/datasets-fivethirtyeight-ffq/tree/umd
[esm-url]: https://github.com/stdlib-js/datasets-fivethirtyeight-ffq/tree/esm
[branches-url]: https://github.com/stdlib-js/datasets-fivethirtyeight-ffq/blob/main/branches.md

[odc-by-1.0]: http://opendatacommons.org/licenses/by/1.0/

[cc-by-4.0]: http://creativecommons.org/licenses/by/4.0/

[apache-license]: https://www.apache.org/licenses/LICENSE-2.0

[csv]: https://tools.ietf.org/html/rfc4180

[fivethirtyeight-nutrition-studies]: https://fivethirtyeight.com/features/you-cant-trust-what-you-read-about-nutrition/

[block-ffq]: https://nutritionquest.com/assessment/list-of-questionnaires-and-screeners/

[ffq]: https://en.wikipedia.org/wiki/Food_frequency_questionnaire

</section>

<!-- /.links -->
