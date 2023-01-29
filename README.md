
## Breakpointy w mapie

``` js

//  Tworzymy mapę, w której określamy nazwy i przyporządkowujemy im wartości
$breakpoints: (
  smartphone: (min-width: 460px),
  smartphone-large: (min-width: 640px),
  tablet: (min-width: 800px),
  tablet-large: (min-width: 1024px),
  desktop-small: (min-width: 1280px),
  desktop-medium: (min-width: 1600px),
  desktop-large: (min-width: 1900px),
);

```

## Media Queries - deklaracja domieszki

``` scss
@mixin mq($breakpoint) {
// przypisanie do zmiennej $size wartości np. (min-width: 640px)
$size: map-get($breakpoints, $breakpoint);
// sprawdzenie czy mapa zwróciła wartość
// jeśli tak, to dadanie zawartości
@if($size) {
  @media #{$size} {
    @content;
   }
}

// jeśi nie, to wyrzucenie błędu
@else {
  @error '"#{$breakpoint}" - Nie mam tej wielkości'
}

}
```

