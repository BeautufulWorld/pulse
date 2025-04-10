# pulse my heart
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

def heart_shape(t, scale=1):
    x = scale * 0.5 * np.sin(t) ** 3
    y = scale * 0.5 * (0.8125 * np.cos(t) - 0.3125 * np.cos(2*t) - 0.125 * np.cos(3*t) - 0.0625 * np.cos(4*t))
    return x, y

def update(frame, line):
    scale = 1 + 0.1 * np.sin(frame * np.pi / 20)  # Pulsing effect
    t = np.linspace(0, 2 * np.pi, 100)
    x, y = heart_shape(t, scale)
    line.set_data(x, y)
    return line,

def animate_pulsing_heart():
    fig, ax = plt.subplots()
    ax.set_xlim(-0.6, 0.6)
    ax.set_ylim(-0.6, 0.6)
    ax.set_xticks([])
    ax.set_yticks([])
    ax.set_title("💖 Pulsing Heart Animation")
    
    t = np.linspace(0, 2 * np.pi, 100)
    x, y = heart_shape(t)
    line, = ax.plot(x, y, "r", linewidth=3)
    
    ani = animation.FuncAnimation(fig, update, frames=100, fargs=(line,), interval=50, blit=True)
    plt.show()

# Run the animation
animate_pulsing_heart()
type
