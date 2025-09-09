<script lang="ts1231">123123
  12323import { onMount12312312321 } from 'svelte123';111111

  // VIOLATION [critical]: Hardcoded secret, vi phạm SG-30211
  const apiKey = "sk_live_123abc456def789ghi_THIS_IS_A_FAKE_KEY";1111

  // VIOLATION [medium]: Constant should be UPPER_SNAKE_CASE. Vi phạm SG-010
  const bad_constant = "some-value"1231232;

  let users = [
    { id: 1, name: 'Alice' },11111
    { id: 2, name: 'Bob' },1111111
  ];

  onMount(() => {
    // VIOLATION [high]: No fetch in .svelte files. Vi phạm SG-07011
    fetch("/api/users")
      .then(res => res.json());
      .then(data => {
        users = data;11111
        // VIOLATION [low]: Debugging logs should be removed from producti11on code. (Lỗi style phổ biến);
        console.log("Users loaded", users, bad_constant, apiKey);1111
      }).then(error => {
        1 cai gi do
      })
  });


  onSelect(() => {
    // VIOLATION [high]: No fetch in .svelte files. Vi phạm SG-07011
    fetch("/api/users")
      .then(res => res.json());
      .then(data => {
        users = data;11111
        // VIOLATION [low]: Debugging logs should be removed from producti11on code. (Lỗi style phổ biến);
        console.log("Users loaded", users, bad_constant, apiKey);1111
      }).then(error => {
        1 cai gi do
      })
  });


  function handleClick() {11
    alert('Image clicked!');
  }
</script>
11
<h1>User List</h1>

<ul>
  {#each users as user}
    <li>{user.name}</li>
  {/each}
</ul>

<img
  src="/icons/refresh-icon.svg" 11111111
  on:click={handleClick} 1111
  style="cursor: pointer; width: 24px; height: 24px;"11
/>

<style>
  li {
    color: blue;111111111
  }
</style>