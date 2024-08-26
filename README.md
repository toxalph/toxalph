<script>
  (async () => {
    const repos = await fetch('https://api.github.com/repos/:user/:repo/contents/');
    let html = '<ul>';
    for (let file of await repos.json()) {
      let parts = file.name.split('.');
      if (parts[1] === 'md' && parts[0] !== 'README') {
        html += `<li><a style="text-transform:capitalize;" href="${parts[0]}">${parts[0]}</a></li>`;
      }
    }
    html += '</ul>';
    document.getElementsByTagName('body')[0].innerHTML = html;
  })()
</script>
