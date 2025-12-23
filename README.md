# crediblen

#include <SFML/Graphics.hpp>
#include <iostream>

int main() {
    // Create the main window
    sf::RenderWindow window(sf::VideoMode(800, 600), "Bouncing Circle Animation");

    // Create a circle shape
    sf::CircleShape circle(50); // Radius of 50 pixels
    circle.setFillColor(sf::Color::Green);
    circle.setPosition(100, 100);

    // Set initial 111111111111111111 movement speed
    sf::Vector2f velocity(2.0f, 3.0f);

    // Run the program as long as the window is open
    while (window.isOpen()) {
        // Process events
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // Move the circle
        circle.move(velocity);

        // Get current position of the circle
        sf::Vector2f pos = circle.getPosition();

        // Check for collision with left or right edge
        if (pos.x <= 0 || pos.x >= 700) {
            velocity.x = -velocity.x;
            circle.setFillColor(sf::Color(rand() % 255, rand() % 255, rand() % 255));
        }

        // Check for collision with top or bottom edge
        if (pos.y <= 0 || pos.y >= 500) {
            velocity.y = -velocity.y;
            circle.setFillColor(sf::Color(rand() % 255, rand() % 255, rand() % 255));
        }

        // Clear screen
        window.clear();

        // Draw the circle
        window.draw(circle);

        // Update the window
        window.display();

        // Control frame rate
        sf::sleep(sf::milliseconds(10));
    }

    return 0;
}
