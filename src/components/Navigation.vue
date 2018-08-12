<template>
  <div>

    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="#">Digital Transformation</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item" id="NavbarHome">
            <a class="nav-link" href="/#/">Home <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item" id="NavbarBlockchain">
            <a class="nav-link" href="/#/blockchain/menu">Blockchain <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item" id="NavbarCybersecurity">
            <a class="nav-link" href="/#/cybersecurity">Cybersecurity</a>
          </li>
          <li class="nav-item dropdown" id="NavbarAI">
            <a class="nav-link dropdown-toggle" href="/#/ai" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              AI
            </a>
            <div class="dropdown-menu" aria-labelledby="navbarDropdown">
              <a class="dropdown-item" href="#">Action</a>
              <a class="dropdown-item" href="#">Another action</a>
              <div class="dropdown-divider"></div>
              <a class="dropdown-item" href="#">Something else here</a>
            </div>
          </li>
          <li class="nav-item" id="NavbarCloud">
            <a class="nav-link disabled" href="/#/cloud">Cloud</a>
          </li>
        </ul>
        <form class="form-inline my-2 my-lg-0">
          <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
          <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
        </form>
      </div>
    </nav>


  </div>
</template>

<script>

export default {
  name: 'Navigation',
  watch:{
      $route (to, from){
        // -- TODO: detect if on same section and avoid recompute   

        console.log('Hello World from global navigation bar!');
        var path = window.location.hash;
        path = path.split('/');
        path = path[1];

        // remove all active menu elements
        document.getElementById('NavbarHome').classList.remove("active");
        document.getElementById('NavbarBlockchain').classList.remove("active");
        document.getElementById('NavbarCybersecurity').classList.remove("active");
        document.getElementById('NavbarAI').classList.remove("active");
        document.getElementById('NavbarCloud').classList.remove("active");

        // add active menu element
        if (path === '') document.getElementById('NavbarHome').classList.add("active");
        else if (path === 'blockchain') document.getElementById('NavbarBlockchain').classList.add("active");
        else if (path === 'cybersecurity') document.getElementById('NavbarCybersecurity').classList.add("active");
        else if (path === 'ai') document.getElementById('NavbarAI').classList.add("active");
        else if (path === 'cloud') document.getElementById('NavbarCloud').classList.add("active");
      }
  }

}
</script>