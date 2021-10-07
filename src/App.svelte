<script>
  let secondHandEl, minsHandEl, hourHandEl

  const setDate = () => {
    const now = new Date()
    const seconds = now.getSeconds()
    const mins = now.getMinutes()
    const hour = now.getHours()

    const secondsDegrees = (seconds / 60) * 360 + 90
    const minsDegrees = (mins / 60) * 360 + (seconds / 60) * 6 + 90
    const hourDegrees = (hour / 12) * 360 + (mins / 60) * 30 + 90

    if (seconds === 0) {
      secondHandEl.style.transition = 'none 0.05s'
    } else {
      secondHandEl.style.transition =
        'all 0.05s cubic-bezier(0.1, 2.7, 0.58, 1)'
    }

    secondHandEl.style.transform = `rotate(${secondsDegrees}deg)`
    minsHandEl.style.transform = `rotate(${minsDegrees}deg)`
    hourHandEl.style.transform = `rotate(${hourDegrees}deg)`
  }

  setInterval(setDate, 1000)
</script>

<main>
  <article>
    <div bind:this={hourHandEl} />
    <div bind:this={minsHandEl} />
    <div bind:this={secondHandEl} />
  </article>
</main>

<style>
  main {
    width: 30rem;
    height: 30rem;
    border: 20px solid white;
    border-radius: 50%;
    margin: 50px auto;
    position: relative;
    padding: 2rem;
    box-shadow: 0 0 0 4px rgba(0, 0, 0, 0.1), inset 0 0 0 3px #efefef,
      inset 0 0 10px black, 0 0 10px rgba(0, 0, 0, 0.2);
  }
  article {
    position: relative;
    width: 100%;
    height: 100%;
    transform: translateY(-3px);
  }
  div {
    width: 50%;
    height: 6px;
    background: black;
    position: absolute;
    top: 50%;
    transform-origin: 100%;
    transform: rotate(90deg);
    transition: all 0.05s;
    transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
  }
</style>
