# React Component Examples

## SVG as React Component

```jsx
// Import the SVG as a React component
import { ReactComponent as WireframeSphere } from '../3D-Elements/Wireframe/wireframe-sphere.svg';

function MyComponent() {
  return (
    <div className="container">
      <h1>Example Implementation</h1>
      <div className="visual-element">
        <WireframeSphere className="rotating-sphere" />
      </div>
    </div>
  );
}

// CSS for animation
// .rotating-sphere {
//   animation: rotate 20s linear infinite;
// }
// @keyframes rotate {
//   from { transform: rotateY(0deg); }
//   to { transform: rotateY(360deg); }
// }
```

## Animated 3D Element

```jsx
import { useState, useEffect } from 'react';
import { ReactComponent as JellyfishFlow } from '../Abstract-Shapes/Organic/jellyfish-flow.svg';

function AnimatedJellyfish() {
  const [animate, setAnimate] = useState(false);
  
  useEffect(() => {
    // Trigger animation after component mounts
    setAnimate(true);
    
    // Animation interval for pulsing effect
    const interval = setInterval(() => {
      setAnimate(prev => !prev);
    }, 3000);
    
    return () => clearInterval(interval);
  }, []);
  
  return (
    <div className="jellyfish-container">
      <JellyfishFlow 
        className={`jellyfish ${animate ? 'pulse' : ''}`} 
        style={{ 
          transition: 'all 1.5s ease-in-out',
          transform: animate ? 'scale(1.05)' : 'scale(1)',
          filter: animate ? 'brightness(1.2)' : 'brightness(1)'
        }}
      />
    </div>
  );
}
```

## Interactive Neon Button

```jsx
import { ReactComponent as NeonButton } from '../UI-Components/Buttons/neon-button.svg';

function InteractiveButton({ onClick, label = 'EXPLORE' }) {
  return (
    <div className="button-wrapper">
      <button 
        className="neon-button-container" 
        onClick={onClick}
        aria-label={label}
      >
        <NeonButton className="neon-button" />
        
        {/* Override button text */}
        <span className="button-text">{label}</span>
      </button>
    </div>
  );
}

// CSS
// .neon-button-container {
//   background: transparent;
//   border: none;
//   padding: 0;
//   cursor: pointer;
//   position: relative;
// }
// 
// .neon-button {
//   transition: filter 0.3s ease;
// }
// 
// .neon-button-container:hover .neon-button,
// .neon-button-container:focus .neon-button {
//   filter: drop-shadow(0 0 10px rgba(0, 240, 255, 0.8));
// }
// 
// .button-text {
//   position: absolute;
//   top: 50%;
//   left: 50%;
//   transform: translate(-50%, -50%);
//   color: white;
//   font-weight: bold;
//   pointer-events: none;
//   text-transform: uppercase;
// }
```

## Data Visualization with Chart

```jsx
import { ReactComponent as HolographicBarChart } from '../Data-Visualization/Charts/holographic-bar-chart.svg';
import { ReactComponent as GraffitiSplatter } from '../Effects/Spray/graffiti-splatter.svg';

function DataDashboard({ title = "Performance Metrics" }) {
  return (
    <div className="dashboard">
      <div className="dashboard-header">
        <h2>{title}</h2>
        {/* Use splatter as decorative element */}
        <GraffitiSplatter className="decorative-splatter" />
      </div>
      
      <div className="chart-container">
        <HolographicBarChart className="primary-chart" />
        <div className="chart-controls">
          <button className="chart-button">Daily</button>
          <button className="chart-button active">Weekly</button>
          <button className="chart-button">Monthly</button>
        </div>
      </div>
    </div>
  );
}
```

## Text with Glitch Effect

```jsx
import { ReactComponent as TextDistortion } from '../Effects/Glitch/text-distortion.svg';

function GlitchHeading({ text = "GLITCH" }) {
  // Note: For dynamic text, you would need to modify the SVG content
  // This example assumes using the predefined text in the SVG
  
  return (
    <div className="glitch-heading">
      <TextDistortion className="glitch-effect" />
      
      {/* If you need to use custom text instead of "GLITCH" */}
      {text !== "GLITCH" && (
        <div className="custom-text-overlay">
          <h1>{text}</h1>
        </div>
      )}
    </div>
  );
}

// CSS
// .glitch-heading {
//   position: relative;
// }
// .custom-text-overlay {
//   position: absolute;
//   top: 0;
//   left: 0;
//   width: 100%;
//   height: 100%;
//   display: flex;
//   align-items: center;
//   justify-content: center;
// }
// .custom-text-overlay h1 {
//   font-family: Arial, sans-serif;
//   font-size: 5rem;
//   text-transform: uppercase;
//   mix-blend-mode: overlay;
// }
```

## Combining Multiple Assets

```jsx
import { ReactComponent as FrequencyWave } from '../Abstract-Shapes/Wave/frequency-wave.svg';
import { ReactComponent as WireframeCube } from '../3D-Elements/Wireframe/wireframe-cube.svg';
import { ReactComponent as NeonButton } from '../UI-Components/Buttons/neon-button.svg';

function HeroSection() {
  return (
    <div className="hero-container">
      <div className="background-elements">
        <FrequencyWave className="wave-element wave-top" />
        <FrequencyWave className="wave-element wave-bottom" />
        <WireframeCube className="cube-element cube-left" />
        <WireframeCube className="cube-element cube-right" />
      </div>
      
      <div className="hero-content">
        <h1 className="hero-title">FUTURE INTERFACE</h1>
        <p className="hero-subtitle">Explore the next generation of digital experiences</p>
        
        <div className="hero-actions">
          <button className="cta-button">
            <NeonButton />
            <span className="button-text">GET STARTED</span>
          </button>
        </div>
      </div>
    </div>
  );
}

// CSS
// .hero-container {
//   position: relative;
//   height: 100vh;
//   overflow: hidden;
//   background-color: #070b14;
// }
// 
// .background-elements {
//   position: absolute;
//   width: 100%;
//   height: 100%;
//   z-index: 0;
// }
// 
// .wave-element {
//   position: absolute;
//   width: 120%;
//   opacity: 0.4;
// }
// 
// .wave-top {
//   top: 10%;
//   left: -10%;
//   transform: rotate(-5deg);
// }
// 
// .wave-bottom {
//   bottom: 10%;
//   left: -10%;
//   transform: rotate(5deg) scaleX(-1);
// }
// 
// .cube-element {
//   position: absolute;
//   width: 30vmin;
//   height: 30vmin;
//   opacity: 0.6;
// }
// 
// .cube-left {
//   top: 20%;
//   left: 10%;
//   animation: float 10s ease-in-out infinite;
// }
// 
// .cube-right {
//   bottom: 15%;
//   right: 10%;
//   animation: float 14s ease-in-out infinite reverse;
// }
// 
// .hero-content {
//   position: relative;
//   z-index: 1;
//   display: flex;
//   flex-direction: column;
//   align-items: center;
//   justify-content: center;
//   height: 100%;
//   padding: 2rem;
//   text-align: center;
// }
// 
// .hero-title {
//   font-size: 5rem;
//   margin-bottom: 1rem;
//   background: linear-gradient(to right, #00f0ff, #ff00ff);
//   -webkit-background-clip: text;
//   color: transparent;
// }
// 
// .hero-subtitle {
//   font-size: 1.5rem;
//   margin-bottom: 3rem;
//   color: rgba(255, 255, 255, 0.8);
// }
// 
// .cta-button {
//   background: transparent;
//   border: none;
//   cursor: pointer;
//   position: relative;
// }
// 
// .button-text {
//   position: absolute;
//   top: 50%;
//   left: 50%;
//   transform: translate(-50%, -50%);
//   color: white;
//   font-weight: bold;
//   pointer-events: none;
// }
// 
// @keyframes float {
//   0%, 100% { transform: translateY(0) rotate(0deg); }
//   50% { transform: translateY(-20px) rotate(5deg); }
// }
```