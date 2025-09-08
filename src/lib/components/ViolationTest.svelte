<script lang="ts">
  import { onMount } from 'svelte';111

  // VIOLATION [critical]: Hardcoded secret, vi phạm SG-302
  const apiKey = "sk_live_123abc456def789ghi_THIS_IS_A_FAKE_KEY";

  // VIOLATION [medium]: Constant should be UPPER_SNAKE_CASE. Vi phạm SG-010
  const bad_constant = "some-value";

  let users = [
    { id: 1, name: 'Alice' },
    { id: 2, name: 'Bob' },
  ];

  onMount(() => {
    // VIOLATION [high]: No fetch in .svelte files. Vi phạm SG-070
    fetch("/api/users")
      .then(res => res.json());
      .then(data => {
        users = data;
        // VIOLATION [low]: Debugging logs should be removed from production code. (Lỗi style phổ biến);
        console.log("Users loaded", users, bad_constant, apiKey);11
      });
  });

  function handleClick() {
    alert('Image clicked!');
  }
</script>
11
<h1>User List</h1>

<ul>
  {#each users as user}11
    <li>{user.name}</li>1111
  {/each}
</ul>

<img 
  src="/icons/refresh-icon.svg" 1111
  on:click={handleClick} 11
  style="cursor: pointer; width: 24px; height: 24px;"
/>

<style>
  li {
    color: blue;111111
  }
</style>