# [jQuery pagination plugin (bootstrap powered)](http://josecebe.github.io/twbs-pagination/)

### Basic usage ###

Plugin requires jQuery (required - 1.7.0 or higher).

You can use Bootstrap CSS styles and markup (or use your own).

The following code shows call the function on `<ul>` tag (it can be also `<div>` tag).

```javascript
$('#pagination-demo').twbsPagination({
  totalPages: 35,
  visiblePages: 7,
  onPageClick: function (event, page) {
    $('#page-content').text('Page ' + page);
  }
});
```

## Contributing
For development use grunt build to make minified file.
To use grunt install packages by using: npm install

## Demo and Docs
~~For more information see [docs on github pages](http://josecebe.github.io/twbs-pagination/) (not completed yet)~~
### Demo

This jQuery plugin simplifies the usage of Bootstrap Pagintion. It uses appropriate classes: .pagination (you change this one), .active and .disabled. Check out the demo.

Page 1

Here is corresponding piece of code:

```
    $('#pagination-demo').twbsPagination({
        totalPages: 35,
        visiblePages: 7,
        onPageClick: function (event, page) {
            $('#page-content').text('Page ' + page);
        }
    });
```

And HTML code:

```
    <ul id="pagination-demo" class="pagination-sm"></ul>
```

Download master:

[Download .zip file ](https://github.com/esimakin/twbs-pagination/zipball/master)[Download .tar.gz file](https://github.com/esimakin/twbs-pagination/tarball/master)

### Options explanation

Option name Description Type Default value

|                        |                                                   |          |                   |
| ---------------------- | ------------------------------------------------- | -------- | ----------------- |
| totalPages             | The number of pages                               | Number   | 1                 |
| startPage              | The current page that show on start               | Number   | 1                 |
| visiblePages           | Max visible pages                                 | Number   | 5                 |
| initiateStartPageClick | Fire click at start page when plugin initialized  | Bool     | true              |
| hideOnlyOnePage        | This hides all control buttons if it has one page | Bool     | false             |
| href                   | Generate query string or generate #               | Bool     | false             |
| pageVariable           | Template that will be replaced with page number   | String   | '{{page}}'        |
| totalPagesVariable     | Will be replaced with total pages number          | String   | '{{total_pages}}' |
| page                   | It can be used to customize page number label     | String   | null              |
| first                  | Text label for the 'First' button                 | String   | 'First'           |
| prev                   | Label for the 'Previous' button                   | String   | 'Previous'        |
| next                   | Label for the 'Next' button                       | String   | 'Next'            |
| last                   | Label for the 'Last' button                       | String   | 'Last'            |
| loop                   | Carousel-style pagination                         | Bool     | false             |
| onPageClick            | Callback on click event                           | Function | null              |
| paginationClass        | The root style for pagination component           | String   | 'pagination'      |
| nextClass              | CSS class(es) for the 'Next' button               | String   | 'page-item next'  |
| prevClass              | Class(es) for the 'Previous' button               | String   | 'page-item prev'  |
| lastClass              | Class(es) for the 'Last' button                   | String   | 'page-item last'  |
| firstClass             | Class(es) for the 'First' button                  | String   | 'page-item first' |
| pageClass              | Class(es) for the page buttons                    | String   | 'page-item'       |
| activeClass            | Class(es) for active button                       | String   | 'active'          |
| disabledClass          | Class(es) for the disabled button(s)              | String   | 'disabled'        |
| anchorClass            | CSS class(es) for anchors inside buttons          | String   | 'page-link'       |



### Examples

#### Dynamic total pages number

This is from frequently asked questions. For e.g. - How can I set new number of total pages? How can I initialize plugin with new set of options? How to refresh or redraw it?

You can do it with two simple steps. Call destroy method and then initialize it with new options.

```
    var $pagination = $('selector');
    var defaultOpts = {
        totalPages: 20
    };
    $pagination.twbsPagination(defaultOpts);
    $.ajax({
        ...,
        success: function (data) {
            var totalPages = data.newTotalPages;
            var currentPage = $pagination.twbsPagination('getCurrentPage');
            $pagination.twbsPagination('destroy');
            $pagination.twbsPagination($.extend({}, defaultOpts, {
                startPage: currentPage,
                totalPages: totalPages
            }));
        }
    });
```

Here you can change the total pages:

Change



#### Synchronized pagination elements

You can attach multiple paginators to your content and access them via class name. The following example show this case.

HTML code:

```
    <ul class="sync-pagination"></ul>
    <div id="content">Page 1</div>
    <ul class="sync-pagination pagination-sm"></ul>
```

JS code:

```
    $('.sync-pagination').twbsPagination({
        totalPages: 20,
        onPageClick: function (evt, page) {
            $('#content').text('Page ' + page);
        }
    });
```



Page 1



#### Bootstrap 4 example (in iframe)

It shows how it look like with bootstrap 4 (version 4.0.0-alpha.4).



#### Alternative style pagination (with start and end page numbers)

For that purpose (see example view) I suggest [flaviusmatis/simplePagination.js](https://github.com/flaviusmatis/simplePagination.js) plugin.

JS code:

```
    $('selector').pagination({
        items: 20,
        itemOnPage: 8,
        currentPage: 1,
        cssStyle: '',
        prevText: '<span aria-hidden="true">&laquo;</span>',
        nextText: '<span aria-hidden="true">&raquo;</span>',
        onInit: function () {
            // fire first page loading
        },
        onPageClick: function (page, evt) {
            // some code
        }
    });
```

Page 1



#### Methods 'enable' and 'disable' in action

Page 1



Push the buttons...

Enable Disable

JS code:

```
    // ### IF YOU DON'T PASS onPageClick FUNCTION IN OPTIONS OBJECT
    // ### YOU SHOULD FIRE FIRST PAGE CLICK INDEPENDENTLY
    // ### BECAUSE PLUGIN DOESN'T HAVE ANY CALLBACK
    // ### TO FIRE IT DURING INITIALIZATION
    var $edPag = $('#enable-disable-pagination').twbsPagination({
        totalPages: 20
    }).on('page', function (evt, page) {
        $('#enable-disable-pagination-content').text('Page ' + page);
    });

    $('#enable-pagination').click(function () {
        $edPag.twbsPagination('enable');
    });

    $('#disable-pagination').click(function () {
        $edPag.twbsPagination('disable');
    });
```

### License

Copyright 2014 Eugene Simakin

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

- [Demo](https://josecebe.github.io/twbs-pagination/#demo)
- [Options explanation](https://josecebe.github.io/twbs-pagination/#options-and-events)
- [Examples](https://josecebe.github.io/twbs-pagination/#examples)
- [License](https://josecebe.github.io/twbs-pagination/#license)
