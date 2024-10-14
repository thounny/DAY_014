# DAY_014 | Tile Grid Animation

This project is part of the daily code challenge series, **DAY_014**, where I explore creating **tile grid animations** that flip on hover and by pressing a button to flip all tiles simultaneously. The project utilizes **HTML**, **CSS**, **JavaScript**, and **GSAP** to handle animations and smooth interactions across a grid of tiles. Each tile flips to reveal another image or GIF, creating dynamic transitions throughout the page.

## Inspiration

This project was inspired by the **JUNNI Corporate Site** (Honorable Mention on Awwwards - Oct 2, 2024). I wanted to recreate their tile-flip effect, experimenting with **GSAP** for handling the smooth animations and interactions across the grid.

---

## Project Preview

![DAY_014 Animation](./assets/DAY_014_2.gif)

## JUNNI Site

![JUNNI Grid Animation](./assets/DAY_014_1.gif)

---

## GSAP in Action

### What is GSAP?

**GSAP (GreenSock Animation Platform)** is a powerful JavaScript library used for creating high-performance animations. It allows for precise control over animations, providing a smooth and responsive experience for users.

### How GSAP is Used in This Project

In **DAY_014**, the animations are triggered by both user interactions (hover) and a button to flip all tiles at once. Hovering over any tile flips it with a smooth animation, while clicking the "Flip All" button flips all the tiles simultaneously.

---

## Detailed Breakdown of the JavaScript

### Key JavaScript Code

#### Button-based flipping

```javascript
const flipButton = document.getElementById("flipButton");
flipButton.addEventListener("click", () => {
  flipAllTiles(tiles);
});
```

The "Flip All" button is selected by its ID, and an event listener is added to listen for clicks. When the button is clicked, it calls the `flipAllTiles()` function, which flips all the tiles on the grid.

#### Hover-based flipping

```javascript
tiles.forEach((tile, index) => {
  tile.addEventListener("mouseenter", () => {
    animateTile(tile, tiltY);
  });
});
```

- For each tile in the grid, an event listener is added to detect when the mouse hovers over it. When the `mouseenter` event occurs, the `animateTile()` function is called, flipping the tile and adding tilt effects.

#### Animate individual tiles

```javascript
function animateTile(tile, tiltY) {
  gsap
    .timeline()
    .set(tile, { rotateX: isFlipped ? 180 : 0, rotateY: 0 })
    .to(tile, {
      rotateX: isFlipped ? 450 : 270,
      rotateY: tiltY,
      duration: 0.5,
      ease: "power2.out",
    })
    .to(
      tile,
      {
        rotateX: isFlipped ? 540 : 360,
        rotateY: 0,
        duration: 0.5,
        ease: "power2.out",
      },
      "-=0.25"
    );
}
```

- This function animates each tile's flip. GSAP’s timeline is used to set the initial rotation of the tile and then apply the rotation animation over time. Depending on whether the tile is flipped or not, it rotates by different degrees (`rotateX: 180` or `rotateX: 0`). The tilt effect (`rotateY: tiltY`) is added to make the animation more dynamic.

#### Flip all tiles

```javascript
function flipAllTiles(tiles) {
  isFlipped = !isFlipped;
  gsap.to(tiles, {
    rotateX: isFlipped ? 180 : 0,
    duration: 1,
    stagger: {
      amount: 0.5,
      from: "random",
    },
    ease: "power2.inOut",
  });
}
```

- This function is responsible for flipping all tiles in the grid at once. GSAP’s `to()` function is used to rotate all the tiles, either flipping them to 180 degrees or back to 0. The `stagger` option is set to create a slight delay between each tile flip, adding a dynamic cascading effect.

---

## How to Run

1. **Clone the repository**:

   ```bash
   git clone https://github.com/thounny/DAY_014.git
   ```

2. **Navigate to the project directory**:

   ```bash
   cd DAY_014
   ```

3. **Open the `index.html` file** in your web browser:

   - You can double-click the file in your file explorer, or
   - Serve it using a local development server (e.g., Live Server in VSCode).

---

## Project Structure

```bash
DAY_014/
│
├── assets/
│   └── favicon.ico
│   └── index_dwn.gif
│   └── miku.gif
│   └── 5.jpg
│   └── 2.gif
│   └── DAY_014_1.gif
│   └── DAY_014_2.gif
├── fonts/
│   └── helveticaneue.woff2
├── styles.css
├── index.html
└── script.js
```

---

## Features

- **Grid-Based Tile Animation**: Hover or press the "Flip All" button to trigger smooth tile flips, revealing images or GIFs.
- **Hover-Based Animations**: The grid reacts to hover interactions, flipping individual tiles.
- **Image and GIF Handling**: Both images and GIFs are used as tile faces, and their aspect ratios are preserved for a consistent display.

---

## Technologies Used

- **HTML5**: For document structure.
- **CSS3**: For grid layout and styling.
- **JavaScript (ES6)**: For handling interactions and animations.
- **GSAP (GreenSock Animation Platform)**: For creating smooth, high-performance animations.

---

## Author

![Logo](./assets/index_dwn.gif)

**Thounny Keo**  
Frontend Development Student | Year Up United

---
![Logo](./assets/miku.gif)
