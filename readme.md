*(forked from our nwhacks 2025 project for personal use)*

## Inspiration

Besides the thrill of having 4 CS students congregate together in a caliginous room in our CS buildings basement working on a project for the next 24 hours, we were excited by the prospect of trying something that most of us hadn't done before - combining hardware and software. More importantly, We saw great potential in our idea, and took to chance to learn new skills to create something that we think will be the future of music streaming.

Imagine you're walking around your house, doing chores, walking around - you know, regular house stuff. You've got your Spotify connected to your speaker system so you can enjoy music whilst doing your daily activities. Suddenly a song comes up, and it's not a Tuesday afternoon song. You want to skip it but your hands are dirty washing dishes, and further, you don't want to go all the way back to your laptop just press some buttons. What if instead you had the power of our product built in right next to you, to just 'paw' over our device and skip your song from afar?

Our team believes there is a certain convenience in controlling something as widely used as Spotify without interacting with your device physically. Hand gestures eliminate the need to physically interact with a device, making it ideal for situations where hands are occupied, such as cooking, exercising, or driving. This approach can benefit individuals with physical disabilities or conditions that make button-pressing difficult.


## What it does

There are some key functionality features of using Spotify: skipping forward, going to the previous song, and pausing and playing. All a user has to do is connect to their Spotify account on their laptop and run our product with our hardware. With three simple gestures, you will find that any user can achieve these key functionalities:

- Skipping forward- move your hand toward the sensor.
- Skip back - move your hand away from the sensor.
- Pause/play - hold your hand close to the sensor.


## How we built it

We programmed an Arduino Uno to receive and process data from an ultrasound sensor which can detect a user's hand and its position relative to the device. This data is then received in a Python script and sent to our backend using our Flask API. Then comes everyone's favourite high school subject - Math! To figure out how a user's hand moves We pass our data into an array and calculate the derivatives of the data over time to determine if our user's hand is moving forward, or backward, which then corresponds to the previous and next song respectively. The processed user input is passed to our Spotify API to control your Spotify.


## Challenges we ran into

In the past 24 hours, we ran into many challenges that all of us had to persevere through to achieve our goals. The first few challenges that we experienced at almost the same time were learning the prerequisite knowledge for using an Arduino, an ultrasonic sensor, the Spotify API, and the Flask API. The way that we overcame this challenge was by splitting our group into two teams: the hardware team and the software team. The hardware team was responsible for becoming masters at using the Arduino and the sensor, and the software team was responsible for becoming masters of the APIs. We then came together to discuss what we learned. 

However, our most difficult challenge came after we integrated everything and had to use the sensor to differentiate between different motions. The Arduino would give us many different values and we needed a way to notice when a hand was going up and down, and when there wasn't a hand at all. We tried a lot of different ideas, including Gaussian smoothing, calculating the derivative, and calculating differences. However, all of these had different drawbacks, whether it was computational cost, low accuracy caused by a small dataset, and so on. The final idea that we had was to split our data into an "old" and "new" set and compare the medians of the values to identify whether the data has changed or not. There are some more details and small issues that this had, but it was the most reliable strategy that we had, and its simplicity is very convenient. 


## What we learned

Throughout this, we learned many different skills that would be beneficial to future projects that we may work on. One of the biggest skills was using hardware tools, such as an Arduino and various sensors, especially the ultrasonic sensor. It was very difficult for us because we all have a CS background and not an engineering one. However, we learned enough of the basics to make a functional product! Along with that, we learned a lot about different trial-and-error techniques and different ways to detect hand motions. Finally, we learned about different API frameworks, and how we could use them to implement the Spotify API as well.


## What's next for SpotiPaw

Of course, due to the time limitations of a hackathon, we won't be able to add every feature we can envision. One of the main features that we want to add in the future is the addition of one more sensor next to the current one. This would allow SpotiPaw to detect left-right movement, allowing SpotiPaw to have even more actions, such as volume up/down. Along with the sensor, such a feature would also require changing our motion detection algorithm to be able to differentiate between left/right, up/down, pause, and random noise.

One other feature that we can add is improved quality of sensors. At the moment, because of the quality of the ultrasonic sensor, we are picking up a lot of background noise that is not ideal. We want to find better sensors that can work with our Arduino that would reduce the sound and allow for more accurate motion detection and improve reliability.

Finally, we could take our product and apply it to more real-life scenarios. SpotiPaw has the ability to be used in many places for many uses. For example, it can be used in a kitchen to change the song while your hands are dirty and you don't want to touch your phone. It can also be integrated into a car to allow for music changes without having to fiddle around with buttons that could be distracting while driving. Overall, SpotiPaw has a lot of potential and we hope to continuously iterate upon it to make it the best it can be.
