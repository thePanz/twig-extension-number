# Twig-Extension-Number

A Twig extension to handle number formatting.

Included filters:
   - `format_bytes` Formats the given amount as bytes and display it in an as a human-readable format.
   The filter supports 1000/1024 base counting and formatting
   - `format_grams` Formats the given amount as "grams" in a human-readable format
   - `format_meters` Formats the given amount as "meters" in a human-readable format

## Examples

Display the value of 4000 grams in a human-readable format (4.00 Kg):
```
{{ 4000 | format_grams }}
```

The filter allows some customization of the output, given its signature `filter_grams(decimals, unityBias)`:
* *Decimals*: Display the value of 4000 grams in a human-readable format with 3 decimals (4.000 Kg):
   ```
   {{ 4000 | format_grams(3) }}
   ```
* *UnityBias*: Set the filter to handle the number as being expressed with a different bias then the standard unit (grams).
  To display the value of 4000 (expressed in milligrams, `1E-3`) as grams in a human-readable format with 3 decimals (4.00 g)
  use:
   ```
   {{ 4000 | format_grams(3, 1E-3) }}
   ```

## Install

In Symfony, tag `Pnz\TwigExtensionNumber\Number` with `twig.extension`, and the filter will be
automatically registered.

```yaml
    # file: config/services.yaml
    Pnz\TwigExtensionNumber\Number:
        tags: ['twig.extension']
```
