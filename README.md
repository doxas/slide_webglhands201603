# slide math 201603

[第6回 プログラマのための数学勉強会 - dots. [ドッツ]](http://eventdots.jp/event/582339)

http://goo.gl/iqckt0

```
precision mediump float;
uniform vec2  resolution;    // resolution (512.0, 512.0)
uniform vec2  mouse;         // mouse      (-1.0 ~ 1.0)
uniform float time;          // time       (1second == 1.0)
uniform sampler2D prevScene; // previous scene texture

const float PI = 3.14159;
const float PI2 = PI * 2.0;
const vec3 fire = vec3(1.0, 0.5, 0.2);

void main(){
    vec2 p = (gl_FragCoord.xy / resolution) * 2.0 - 1.0;
    float s = sin(time * 0.5 * sin(length(p)));
    float c = cos(time * 0.7 * cos(length(p)));
    mat2 m = mat2(c, -s, s, c);
    vec2 q = m * p;
    float r = 0.5 / abs(sin(length(q * 50.0) - time * 10.0));
    float g = 0.5 / abs(sin(length(q * 50.0) - time * 15.0));
    float b = 0.5 / abs(sin(length(q * 50.0) - time * 20.0));
    float f = pow(2.0 - length(q), 5.0);
    float w = (atan(q.y, q.x) + PI) / PI2;
    float x = abs(sin(w * 100.0));
    gl_FragColor = vec4(vec3(r, g, b) * f * fire * x, 1.0);
}
```

