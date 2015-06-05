### Local shortcodes

Register and run shortcodes within a local namespace.

This avoids competing with shortcode names used by other themes and plugins.

## Usage

###### Register

Declare your chosen namespace, local shortcode name and function.

```
add_local_shortcode('context', 'local', 'local_shortcode');
```

###### Run

Run local shortcodes registered under the namespace.

```
do_local_shortcode('context', $content);
```

###### Run global shortcodes also

```
do_local_shortcode('context', $content, true);
```

###### Unregister

Unregister a local shortcode within the given namespace.

```
remove_local_shortcode('context', 'local');
```

###### Unregister all within context

Unregister all local shortcodes within the given namespace.

```
remove_all_local_shortcodes('context');
```
   
## Example
   
###### Inside post

```
[parent]

  [child]

[/parent]
```

###### Inside parent shortcode

```
// Register parent shortcode in global namespace
add_shortcode('parent', 'parent_shortcode');

// Register child shortcode in local namespace
add_local_shortcode('parent', 'child', 'child_shortcode');

function parent_shortcode( $atts, $content ) {

  ...Do stuff here..

  return do_local_shortcode('parent', $content);
}

function child_shortcode( $atts, $content ) {

  ...Do stuff here..

}
```
