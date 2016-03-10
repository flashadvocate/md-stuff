Proposing a shortcode to be included in this project is a pretty straightforward process.

#### 1.  Shortcodes have a single responsibility

Each of the current shortcodes were approached with the mentality that they would, in the simplest terms, fulfill a single requirement, or provide a single functionality. The naming convention lends to this mentality. The 'Button' provides a shortcode for generating a button element. Although not all-encompassing, the shortcode allows for a variety of variations. All shortcodes should follow a similar practice.

In other words, shortcodes should not include multiple functions. We would simply create a separate shortcode.



#### 2. Follow PSR1/PSR2 Coding Style

For arguable (but not debatable) reasons, we do not follow WordPress's PHP coding standards. Instead, we defer to [**PSR1/PSR2**](http://www.php-fig.org/psr/psr-2/) because well... we can. It's also very easy to incorporate PSR2 coding style into PHPStorm, so this shouldn't be a huge deal.

However, we **will** defer to WordPress's Coding Standards for 
* [**JavaScript**](https://make.wordpress.org/core/handbook/best-practices/coding-standards/javascript/)
* [**HTML**](https://make.wordpress.org/core/handbook/best-practices/coding-standards/html/)



#### 3. SASS instead of CSS

To stay consistent, we ask that all contributions utilize SASS (SCSS). CSS files will be stored in either `public/css/sass/shortcodes/class-yourshortcode.scss` or `admin/css/sass/shortcodes/class-yourshortcode.scss`. All SCSS will be compiled down and enqueued by the plugin; you do not have enqueue them via your shortcode class.




#### 4. Enqueue JS resources individually.

Should your shortcode need to make use of JS, store scripts in the appropriate `public/js/shortcodes/` or `admin/js/shortcodes` directory, and enqueue them with the necessary action hook. 

_Note: if you are using event listeners to handle conditional display of Shortcake UI fields, use the `enqueue_shortcode_ui` action to enqueue your JS. _




#### 5. Extend the Shortcode Class

To ensure that shortcodes are consistent, and that they are compatible with Shortcake UI, extend the Shortcode abstract class (`inc/shortcodes/class-shortcode.php`) in your shortcode class. At a minimum, you must implement the `get_shortcode_ui_args()` and `callback()` methods in order for the shortcode to work properly with Shortcake. 

We ask that you also use the `get_attributes()` method to keep things tidy, and of course extract to additional methods as needed. The `reversal()` method is used to provide conversion of an HTML tag into the provided shortcode (if it exists).

Review the `class-button.php` shortcode for reference.




#### 6. Provide adequate comments

This should go without saying, but please include appropriate PHPDoc comments for your methods.




#### 6. Testing (coming soon™)

We obviously currently are not pushing TDD at this point. We do plan to make use of PHPUnit testing in the near future and will at that point require all future contributions to include tests for their respective shortcode class. It would be fantastic if any current contributors update their shortcode as needed. It's just the right thing to do.
