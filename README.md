


## Breakpointy w mapie

``` scss
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

## Co to jest lazy loading:

Lazy loading grafik to późnienie wczytywania zasobów do momentu, w którym
rzeczywiście będą one potrzebne. W praktyce grafiki będą wczytywane dopiero
wtedy, kiedy mogą być potrzebne, czyli przede wszystkim wtedy gdy obszar
viewportu znajdzie się blisko danego obrazu.

Korzyść? Nie zapychamy łącza i zasobów użytkownika (i własnego serwera) póki
nie jest to potrzebne. Być może nigdy nie będzie, bo użytkownik nie przewinie
strony do miejsca gdzie grafika jest potrzebna, po co więc wczytywać wszystko.

Lazy loading najczęściej rozwiązywany jest poprzez JavaScript, ale możemy też
od niedawna (31.07.2019) korzytać z natywnego wsparcia przeglądarek (póki co
Chrome) dla lazy loadingu.
