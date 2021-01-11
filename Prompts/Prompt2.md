# Prompt 2: Working with Props
In the `React` project you created in `Prompt 1`, please fullfil the requirements below:
- Create a directory named `components`
- Inside the components directory create another directory called Prompt 2
- Inside of the Prompt 2 directory create two `Class` components:
  1. SongData
  2. SingThatSing
- In the `SongData` component declare the three following variables:
```jsx
        let title = 'September'
        let lyrics = `Do you remember, 21st night of September?
        Love was changing the mind of pretenders
        While chasing the clouds away
        Our hearts were ringing
        In the key that our souls were singing
        As we danced in the night
        Remember
        How the stars stole the night away, oh yeah
`
        let artist = 'Earth Wind and Fire'
```
- Render the `SingThatSong` component inside the `SongData` component
- Pass all three variables (`title`, `lyrics`, `artist`) as separate props to the `SingThatSong` component
- Inside the `SingThatSong` component deconstruct the props **and** render each in the following way:
  - Display the song `title` in a h1 tag
  - Display the `artist` in a h2 tag
  - Display the `lyrics` in a p tag
- Render the `SongData` component inside of the `App` Component