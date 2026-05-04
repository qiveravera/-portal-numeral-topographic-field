<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Portal Numeral: Topographic Field</title>
    <style>
        :root {
            --bg-color: #000000;
            --text-color: #ffffff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body, html {
            width: 100%;
            height: 100%;
            background-color: var(--bg-color);
            overflow: hidden;
            font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
        }

        #app-container {
            position: relative;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        #glcanvas {
            position: absolute;
            inset: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        #text-mask {
            position: absolute;
            inset: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: clamp(150px, 45vw, 85vh);
            font-weight: 900;
            letter-spacing: -0.04em;
            background-color: var(--bg-color);
            color: var(--text-color);
            mix-blend-mode: multiply;
            z-index: 2;
            pointer-events: none;
            user-select: none;
            line-height: 1;
            transition: transform 0.08s cubic-bezier(0.1, 0.7, 0.1, 1);
        }

        #text-mask.bump {
            transform: scale(0.96);
        }

        #ui-selector {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 20px;
            z-index: 10;
            background: rgba(0, 0, 0, 0.5);
            padding: 10px 20px;
            border-radius: 30px;
            backdrop-filter: blur(4px);
        }

        .digit-btn {
            background: none;
            border: none;
            color: rgba(255, 255, 255, 0.3);
            font-family: inherit;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: color 0.3s ease, transform 0.2s ease;
            padding: 5px;
        }

        .digit-btn:hover {
            color: rgba(255, 255, 255, 0.8);
        }

        .digit-btn.active {
            color: rgba(255, 255, 255, 1);
            transform: scale(1.2);
        }
    </style>
</head>
<body>

    <div id="app-container">
        <!-- Generative Field -->
        <canvas id="glcanvas"></canvas>
        
        <!-- Portal Mask -->
        <div id="text-mask">7</div>
        
        <!-- UI -->
        <div id="ui-selector">
            <button class="digit-btn" data-val="1">1</button>
            <button class="digit-btn" data-val="2">2</button>
            <button class="digit-btn" data-val="3">3</button>
            <button class="digit-btn" data-val="4">4</button>
            <button class="digit-btn" data-val="5">5</button>
            <button class="digit-btn" data-val="6">6</button>
            <button class="digit-btn active" data-val="7">7</button>
            <button class="digit-btn" data-val="8">8</button>
            <button class="digit-btn" data-val="9">9</button>
            <button class="digit-btn" data-val="10">10</button>
        </div>
    </div>

    <script>
        /**
         * PORTAL NUMERAL: TOPOGRAPHIC FIELD
         * Version 2: Refined Cartographic Lines & Distinct Structural Topologies
         */

        function initApp() {
            const canvas = document.getElementById('glcanvas');
            const gl = canvas.getContext('webgl') || canvas.getContext('experimental-webgl');
            const textMask = document.getElementById('text-mask');
            const buttons = document.querySelectorAll('.digit-btn');

            // --- CHANGED: WebGL Fallback Safety ---
            // If WebGL fails, we halt script execution here and setup a pure CSS/DOM fallback.
            if (!gl) {
                console.warn("WebGL is not supported. Activating static fallback.");
                textMask.style.mixBlendMode = 'normal'; // Show white text
                canvas.style.display = 'none'; // Hide broken canvas
                
                // Fallback UI logic
                buttons.forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        textMask.innerText = e.target.getAttribute('data-val');
                        buttons.forEach(b => b.classList.remove('active'));
                        e.target.classList.add('active');
                    });
                });
                return; // Prevent shader compilation and render loop
            }

            // Vertex Shader: Fullscreen quad
            const vsSource = `
                attribute vec2 a_position;
                varying vec2 v_uv;
                void main() {
                    v_uv = a_position * 0.5 + 0.5; // Map -1..1 to 0..1
                    gl_Position = vec4(a_position, 0.0, 1.0);
                }
            `;

            // Fragment Shader: Generative Topography Core
            const fsSource = `
                precision highp float;
                varying vec2 v_uv;
                uniform float u_time;
                uniform vec2 u_mouse;
                uniform float u_number;
                uniform vec2 u_resolution;

                // 2D Hash function for noise
                vec2 hash(vec2 p) {
                    p = vec2(dot(p, vec2(127.1, 311.7)), dot(p, vec2(269.5, 183.3)));
                    return -1.0 + 2.0 * fract(sin(p) * 43758.5453123);
                }

                // Simplex-style noise approximation
                float noise(in vec2 p) {
                    const float K1 = 0.366025404; 
                    const float K2 = 0.211324865; 
                    vec2 i = floor(p + (p.x + p.y) * K1);
                    vec2 a = p - i + (i.x + i.y) * K2;
                    vec2 o = (a.x > a.y) ? vec2(1.0, 0.0) : vec2(0.0, 1.0);
                    vec2 b = a - o + K2;
                    vec2 c = a - 1.0 + 2.0 * K2;
                    vec3 h = max(0.5 - vec3(dot(a, a), dot(b, b), dot(c, c)), 0.0);
                    vec3 n = h * h * h * h * vec3(dot(a, hash(i + 0.0)), dot(b, hash(i + o)), dot(c, hash(i + 1.0)));
                    return dot(n, vec3(70.0));
                }

                // Fractal Brownian Motion
                float fbm(vec2 uv) {
                    float f = 0.0;
                    float amp = 0.5;
                    for(int i = 0; i < 4; i++) {
                        f += amp * noise(uv);
                        uv *= 2.0;
                        amp *= 0.5;
                    }
                    return f;
                }

                void main() {
                    vec2 uv = v_uv;
                    float aspect = u_resolution.x / u_resolution.y;
                    uv.x *= aspect;
                    uv -= vec2(0.5 * aspect, 0.5); 

                    vec2 mOffset = (u_mouse - 0.5) * 2.0;
                    uv += mOffset * 0.05;

                    float d = 0.0;
                    float n = u_number;

                    // --- CHANGED: Exaggerated Structural Topologies ---
                    if (n < 1.5) { 
                        // 1: Single strong vortex / funnel (Spiral Archimedean-style)
                        float angle = atan(uv.y, uv.x);
                        float radius = length(uv);
                        d = radius * 3.0 + sin(angle * 3.0 + radius * 10.0 - u_time * 0.5) * 0.3;
                    } else if (n < 2.5) { 
                        // 2: Dual opposing vortices (Dipole)
                        d = length(uv - vec2(-0.3, 0.0)) - length(uv - vec2(0.3, 0.0));
                    } else if (n < 3.5) { 
                        // 3: Precise grid / lattice structure
                        d = abs(cos(uv.x * 8.0)) + abs(cos(uv.y * 8.0));
                    } else if (n < 4.5) { 
                        // 4: Architectural diamond pressure
                        d = abs(uv.x) + abs(uv.y);
                    } else if (n < 5.5) { 
                        // 5: Radial five-point symmetry
                        float angle = atan(uv.y, uv.x);
                        d = length(uv) + cos(angle * 5.0) * 0.2;
                    } else if (n < 6.5) { 
                        // 6: Wavy Topographic bands
                        float angle = atan(uv.y, uv.x);
                        float radius = length(uv);
                        d = radius * 4.0 + sin(angle * 4.0 - radius * 4.0) * 0.2;
                    } else if (n < 7.5) { 
                        // 7: Strong diagonal shear field
                        d = uv.x * 1.5 + uv.y * 2.0;
                    } else if (n < 8.5) { 
                        // 8: Double loop / Infinity well
                        d = length(vec2(abs(uv.x) - 0.4, uv.y));
                    } else if (n < 9.5) { 
                        // 9: Organic core fluctuation
                        d = length(uv) + fbm(uv * 3.0 + u_time * 0.2) * 0.3;
                    } else { 
                        // 10: Clearly dual-field / two-center system (Cassini Ovals)
                        float d1 = length(uv - vec2(-0.4, 0.0));
                        float d2 = length(uv - vec2(0.4, 0.0));
                        d = d1 * d2 * 8.0; 
                    }

                    // Mouse Interaction: Field Pressure
                    float pressure = length(mOffset);
                    
                    // --- CHANGED: Reduced noise impact for sharper, cartographic look ---
                    float nVal = fbm(uv * 2.5 - u_time * 0.1); 
                    float field = d + nVal * (0.1 + pressure * 0.2); // Structure dominates over noise

                    // Density of contour lines
                    float density = 10.0 + pressure * 25.0; 
                    float val = field * density;

                    // --- CHANGED: Cartographic Major/Minor Lines System ---
                    // Distance to nearest whole number creates sharp lines instead of soft waves
                    float lineThickness = 1.0 / density; // Adaptive thickness so it doesn't blob up
                    
                    // Minor contour lines (faint)
                    float dIntMinor = min(fract(val), 1.0 - fract(val)); 
                    float minorLine = smoothstep(lineThickness, 0.0, dIntMinor);
                    
                    // Major contour lines (every 5th line, bolder)
                    float dIntMajor = min(fract(val * 0.2), 1.0 - fract(val * 0.2));
                    float majorLine = smoothstep(lineThickness * 0.8, 0.0, dIntMajor);

                    // Combine and establish strict high-contrast hierarchy
                    float finalIntensity = max(minorLine * 0.25, majorLine);

                    // Depth attenuation (focuses brightness towards center)
                    float depth = smoothstep(2.5, 0.2, length(uv));

                    // Final monochromatic premium color out
                    vec3 color = vec3(finalIntensity * depth);
                    gl_FragColor = vec4(color, 1.0);
                }
            `;

            // Shader Compilation Utility
            function compileShader(gl, type, source) {
                const shader = gl.createShader(type);
                gl.shaderSource(shader, source);
                gl.compileShader(shader);
                if (!gl.getShaderParameter(shader, gl.COMPILE_STATUS)) {
                    console.error('Shader compilation failed:', gl.getShaderInfoLog(shader));
                    gl.deleteShader(shader);
                    return null;
                }
                return shader;
            }

            const vertexShader = compileShader(gl, gl.VERTEX_SHADER, vsSource);
            const fragmentShader = compileShader(gl, gl.FRAGMENT_SHADER, fsSource);

            const program = gl.createProgram();
            gl.attachShader(program, vertexShader);
            gl.attachShader(program, fragmentShader);
            gl.linkProgram(program);

            if (!gl.getProgramParameter(program, gl.LINK_STATUS)) {
                console.error('Program linking failed:', gl.getProgramInfoLog(program));
            }
            gl.useProgram(program);

            // Define a full-screen quad
            const vertices = new Float32Array([
                -1.0, -1.0,  1.0, -1.0,  -1.0,  1.0,
                -1.0,  1.0,  1.0, -1.0,   1.0,  1.0
            ]);

            const positionBuffer = gl.createBuffer();
            gl.bindBuffer(gl.ARRAY_BUFFER, positionBuffer);
            gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW);

            const positionLocation = gl.getAttribLocation(program, 'a_position');
            gl.enableVertexAttribArray(positionLocation);
            gl.vertexAttribPointer(positionLocation, 2, gl.FLOAT, false, 0, 0);

            // Uniform Locations
            const uTimeLoc = gl.getUniformLocation(program, 'u_time');
            const uMouseLoc = gl.getUniformLocation(program, 'u_mouse');
            const uNumberLoc = gl.getUniformLocation(program, 'u_number');
            const uResolutionLoc = gl.getUniformLocation(program, 'u_resolution');

            // Interaction & State Management
            let currentNumber = 7;
            let targetMouse = { x: 0.5, y: 0.5 };
            let currentMouse = { x: 0.5, y: 0.5 };
            let startTime = performance.now();
            
            // Performance Safeguard Variables
            let dpr = Math.min(window.devicePixelRatio, 2.0); 
            let frameCount = 0;
            let lastFpsTime = performance.now();
            let isDowngraded = false;

            function resize() {
                canvas.width = window.innerWidth * dpr;
                canvas.height = window.innerHeight * dpr;
                gl.viewport(0, 0, canvas.width, canvas.height);
            }
            window.addEventListener('resize', resize);
            resize();

            // Mouse Tracker
            window.addEventListener('mousemove', (e) => {
                targetMouse.x = e.clientX / window.innerWidth;
                targetMouse.y = 1.0 - (e.clientY / window.innerHeight);
            });
            
            window.addEventListener('touchmove', (e) => {
                targetMouse.x = e.touches[0].clientX / window.innerWidth;
                targetMouse.y = 1.0 - (e.touches[0].clientY / window.innerHeight);
            }, { passive: true });

            // UI Logic
            buttons.forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const val = e.target.getAttribute('data-val');
                    currentNumber = parseFloat(val);
                    
                    textMask.innerText = val;
                    textMask.classList.remove('bump');
                    void textMask.offsetWidth; 
                    textMask.classList.add('bump');

                    buttons.forEach(b => b.classList.remove('active'));
                    e.target.classList.add('active');
                });
            });

            // Render Loop
            function render(time) {
                currentMouse.x += (targetMouse.x - currentMouse.x) * 0.05;
                currentMouse.y += (targetMouse.y - currentMouse.y) * 0.05;

                gl.uniform1f(uTimeLoc, (time - startTime) * 0.001);
                gl.uniform2f(uMouseLoc, currentMouse.x, currentMouse.y);
                gl.uniform1f(uNumberLoc, currentNumber);
                gl.uniform2f(uResolutionLoc, canvas.width, canvas.height);

                gl.drawArrays(gl.TRIANGLES, 0, 6);

                // Automatic Performance Safeguard
                frameCount++;
                if (frameCount > 60 && !isDowngraded) {
                    let delta = time - lastFpsTime;
                    if (delta > 35) { // Drop DPR if < 30FPS detected over ~1 sec
                        dpr = 1.0; 
                        resize();
                        isDowngraded = true;
                        console.log("Performance optimal mode activated: DPR reduced.");
                    }
                    frameCount = 0;
                    lastFpsTime = time;
                } else if (frameCount > 60) {
                    lastFpsTime = time;
                    frameCount = 0;
                }

                requestAnimationFrame(render);
            }

            requestAnimationFrame(render);
        }

        // Initialize application robustly
        window.onload = initApp;

    </script>
</body>
</html>
