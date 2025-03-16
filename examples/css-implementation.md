# CSS Implementation Examples

## Using SVG as Background

```css
.hero-section {
  position: relative;
  height: 100vh;
  width: 100%;
  overflow: hidden;
  background-color: #070b14;
}

.hero-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('../Abstract-Shapes/Wave/frequency-wave.svg');
  background-size: cover;
  background-position: center;
  opacity: 0.3;
  z-index: 0;
}

.hero-content {
  position: relative;
  z-index: 1;
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
  color: #ffffff;
}
```

## Animated Glow Effect

```css
.glow-button {
  position: relative;
  padding: 12px 24px;
  background-color: transparent;
  color: #00f0ff;
  border: 2px solid #00f0ff;
  border-radius: 4px;
  font-weight: bold;
  overflow: hidden;
  transition: all 0.3s ease;
}

.glow-button::before {
  content: '';
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: #00f0ff;
  z-index: -1;
  filter: blur(15px);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.glow-button:hover::before {
  opacity: 0.7;
}

.glow-button:hover {
  color: #070b14;
  background-color: #00f0ff;
  box-shadow: 0 0 20px rgba(0, 240, 255, 0.5);
}
```

## Glitch Text Effect

```css
.glitch-text {
  position: relative;
  font-size: 4rem;
  font-weight: bold;
  text-transform: uppercase;
  color: white;
}

.glitch-text::before,
.glitch-text::after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0.8;
}

.glitch-text::before {
  left: 2px;
  text-shadow: -1px 0 #ff00ff;
  clip: rect(44px, 450px, 56px, 0);
  animation: glitch-anim 5s infinite linear alternate-reverse;
}

.glitch-text::after {
  left: -2px;
  text-shadow: -1px 0 #00f0ff;
  clip: rect(44px, 450px, 56px, 0);
  animation: glitch-anim2 5s infinite linear alternate-reverse;
}

@keyframes glitch-anim {
  0% {
    clip: rect(23px, 9999px, 68px, 0);
    transform: skew(0.52deg);
  }
  5% {
    clip: rect(79px, 9999px, 31px, 0);
    transform: skew(0.95deg);
  }
  10% {
    clip: rect(15px, 9999px, 90px, 0);
    transform: skew(0.37deg);
  }
  /* Additional keyframes */
  100% {
    clip: rect(97px, 9999px, 89px, 0);
    transform: skew(0.61deg);
  }
}

@keyframes glitch-anim2 {
  0% {
    clip: rect(57px, 9999px, 34px, 0);
    transform: skew(0.49deg);
  }
  /* Additional keyframes */
  100% {
    clip: rect(60px, 9999px, 99px, 0);
    transform: skew(0.27deg);
  }
}
```

## Animated SVG Background

```css
.dynamic-background {
  position: relative;
  overflow: hidden;
  background-color: #070b14;
}

.background-svg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
}

.wireframe-sphere {
  position: absolute;
  width: 40vmin;
  height: 40vmin;
  opacity: 0.4;
  animation: rotate 30s linear infinite;
}

.wireframe-sphere:nth-child(1) {
  top: 10%;
  left: 10%;
}

.wireframe-sphere:nth-child(2) {
  bottom: 10%;
  right: 10%;
  animation-duration: 25s;
  animation-direction: reverse;
}

.jellyfish-flow {
  position: absolute;
  width: 30vmin;
  height: 30vmin;
  opacity: 0.6;
  animation: float 10s ease-in-out infinite;
}

.jellyfish-flow:nth-child(1) {
  top: 30%;
  left: 60%;
}

.jellyfish-flow:nth-child(2) {
  bottom: 30%;
  left: 20%;
  animation-delay: -5s;
}

@keyframes rotate {
  from { transform: rotate3d(1, 1, 1, 0deg); }
  to { transform: rotate3d(1, 1, 1, 360deg); }
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
}
```

## Responsive SVG Layout

```css
.svg-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.svg-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  background-color: rgba(0, 0, 0, 0.3);
  border: 1px solid rgba(0, 240, 255, 0.2);
  border-radius: 8px;
  transition: all 0.3s ease;
}

.svg-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
  border-color: rgba(0, 240, 255, 0.6);
}

.svg-icon {
  width: 100px;
  height: 100px;
  margin-bottom: 1.5rem;
  transition: all 0.3s ease;
}

.svg-card:hover .svg-icon {
  filter: drop-shadow(0 0 10px rgba(0, 240, 255, 0.6));
}

.svg-title {
  font-size: 1.5rem;
  color: #ffffff;
  margin-bottom: 1rem;
}

.svg-description {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.7);
  text-align: center;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .svg-grid {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1.5rem;
    padding: 1.5rem;
  }
  
  .svg-card {
    padding: 1.5rem;
  }
  
  .svg-icon {
    width: 80px;
    height: 80px;
  }
  
  .svg-title {
    font-size: 1.25rem;
  }
}
```

## Data Visualization Styling

```css
.data-dashboard {
  background-color: #0e1b33;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.dashboard-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 2rem;
  position: relative;
}

.dashboard-title {
  font-size: 1.75rem;
  color: #ffffff;
  margin: 0;
}

.chart-container {
  position: relative;
  background-color: rgba(0, 0, 0, 0.2);
  border-radius: 4px;
  overflow: hidden;
  padding: 1.5rem;
}

.chart-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: 
    linear-gradient(0deg, rgba(0, 240, 255, 0.05) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0, 240, 255, 0.05) 1px, transparent 1px);
  background-size: 20px 20px;
  z-index: 0;
}

.holographic-chart {
  position: relative;
  z-index: 1;
  width: 100%;
  height: auto;
  max-height: 300px;
}

.chart-controls {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-top: 1.5rem;
}

.chart-button {
  background-color: transparent;
  color: rgba(255, 255, 255, 0.7);
  border: 1px solid rgba(0, 240, 255, 0.3);
  border-radius: 4px;
  padding: 0.5rem 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.chart-button:hover {
  background-color: rgba(0, 240, 255, 0.1);
  color: white;
}

.chart-button.active {
  background-color: rgba(0, 240, 255, 0.2);
  color: white;
  border-color: rgba(0, 240, 255, 0.6);
}
```

## Retrofuturistic Card Layout

```css
.retrofuture-cards {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  justify-content: center;
  padding: 2rem;
}

.card {
  position: relative;
  width: 300px;
  height: 400px;
  background-color: rgba(0, 0, 0, 0.4);
  border: 1px solid rgba(0, 240, 255, 0.2);
  border-radius: 8px;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    135deg,
    rgba(0, 240, 255, 0.1) 0%,
    rgba(0, 0, 0, 0) 50%,
    rgba(255, 0, 255, 0.1) 100%
  );
  z-index: 1;
  opacity: 0.5;
  transition: opacity 0.4s ease;
}

.card:hover {
  transform: translateY(-10px) scale(1.03);
  border-color: rgba(0, 240, 255, 0.6);
  box-shadow: 
    0 10px 20px rgba(0, 0, 0, 0.2),
    0 0 20px rgba(0, 240, 255, 0.4);
}

.card:hover::before {
  opacity: 0.8;
}

.card-header {
  position: relative;
  height: 160px;
  overflow: hidden;
  border-bottom: 1px solid rgba(0, 240, 255, 0.2);
}

.card-header svg {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 0;
}

.card-body {
  padding: 1.5rem;
  position: relative;
  z-index: 2;
}

.card-title {
  font-size: 1.5rem;
  color: white;
  margin-bottom: 0.5rem;
  position: relative;
}

.card-title::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 50px;
  height: 2px;
  background: linear-gradient(to right, #00f0ff, transparent);
}

.card-description {
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
  line-height: 1.5;
}

.card-action {
  text-align: center;
}

.card-btn {
  background-color: transparent;
  color: #00f0ff;
  border: 1px solid #00f0ff;
  padding: 0.75rem 1.5rem;
  cursor: pointer;
  border-radius: 4px;
  transition: all 0.3s ease;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 1px;
}

.card-btn:hover {
  background-color: rgba(0, 240, 255, 0.1);
  box-shadow: 0 0 10px rgba(0, 240, 255, 0.5);
}
```
