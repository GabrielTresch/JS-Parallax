# JS-Parallax

In order to use the parallax you will have to put the data-speed on the you want

```
 <div data-speed="0.5" class="carre"></div>
```

The script used to make the parallax work

```
var paraEl = document.querySelectorAll("[data-speed]");
const parallax = () =>{
    paraEl.forEach(e=>{	
        var rect = e.getBoundingClientRect();
        var transY = e.dataset.offset || 0;
        var posiOrigin = rect.top - transY + rect.height/2;
        var offset = (posiOrigin - window.innerHeight / 2) * e.dataset.speed;

        if(rect.top < window.innerHeight || 
            offset < window.innerHeight/2){
            e.dataset.offset = offset;
            e.style.transform = `translateY(${offset}px)`;
        }
    })
}
window.addEventListener("scroll", parallax, {passive: true});
parallax();

```
