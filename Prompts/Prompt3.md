# Prompt 3: Working with State
In the `React` project you created in `Prompt 1`, please fullfil the requirements below:
- Inside the `components` directory create another directory called Prompt 3
- Inside of the Prompt 3 directory create two `Class` components:
  1. Station
  2. ShipInfo
- In the `Station` component instantiate `state` and declare three properties with the following data:
```jsx
  shipName = "The Rocinante",
  currentStation = "Tyco Station",
  crewMembers = [
      'Captain James Holden',
      'Executive Officer Naomi Nagata',
      'Pilot Alex Kamal',
      'Chief Engineer Amos Burton'
  ]
```
- Deconstruct all three properties from within the `Station` component's `state`
- Inside the `Station` component display the follow statement in a `h1` and be sure to pass in the corresponding data from `state`:
  - `Here is the Crew Manifest for the <Ship Name Goes Here>`
- Render the `ShipInfo` component inside the `Station` component below the `h1` tag you just created
- Pass the two remaining properties (`currentStation`, and `crewMember`) as separate props to the `ShipInfo` component
- Inside the `ShipInfo` component deconstruct the props **and** render each in the following way:
  - Iterate over the `crewMember` prop and render a `li` for each member of the Roci's crew
  - Display the follow statement in a `h3` and be sure to pass in the corresponding data from `props`:
  - `Currently taking on repairs at: <Current Station Goes Here>`
- Render the `Station` component inside of the `App` Component