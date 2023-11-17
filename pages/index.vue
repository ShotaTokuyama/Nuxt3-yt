<template>
  <h1>TOP</h1>
  <nav id="breadcrumbs">
    <ul>
      <li>Top</li>
    </ul>
  </nav>
  <section>
    <NuxtLink :to="{ name: 'character-characterList' }">キャラクターの設定はこちら</NuxtLink>
  </section>
</template>

<style>
main {
  border: black 5px solid;
  padding: 10px;
}

#breadcrumbs ul {
  padding-left: 0;
}

#breadcrumbs ul li {
  display: inline;
  list-style-type: none;
}

#breadcrumbs ul li::before {
  content: " > ";
}

#breadcrumbs ul li:first-child::before {
  content: none;
}
</style>