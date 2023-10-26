## Why Redux ❔

Because It help you manage the state in only one place(Redux Store). And every component can access the state from that place (Redux Store). **Single Source of Truth**

![[ecommerce mock.png]]

![[eceomerce component.png]]
## Lifting State Up

Often, several components need to reflect the same changing data. We recommend lifting the shared state up to their closest common ancestor

## Solution 

![[all components interact.png]]

# Working of Redux (Flow of Redux)

Type of action ---> increase quantity
Extra Information (payload) ---> current quantity = 1

![[working of redux.png]]