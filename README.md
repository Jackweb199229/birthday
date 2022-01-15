

$(function(){

    setTimeout(function(){
    $('.giftPage').css("display","none");
    $('.greetCard').css("display","flex");
},3000);
window.addEventListener('click', function(e){
    firework(e.clientX, e.clientY);
audio.play();
    
});

var audio=document.getElementById("Audio");


function firework(x,y){
    var firework = document.createElement("DIV");
    firework.className = 'firework';
    document.body.appendChild(firework);
    var posx = window.innerWidth / 2;
    var posy = window.innerHeight * 0.96;
   var color = `rgb(${Math.random()* 255},${Math.random()* 255},${Math.random()* 255})`;
    firework.style.top = posx + 'px';
    firework.style.left = posy +'px';
    firework.style.background = color;
    
    
    function update(){
        posy -= (posy - y) * .05;
        posx -= (posx - x) * .05;
        firework.style.top = posy +'px';
        firework.style.left = posx +'px';
        if (posy - y < 12) {
        firework.style.filter = 'blur(.5vmax)';
    }
    if (posy - y < 2){
        firework.remove();
        for(var i =0; i < 60; i++){
        explode(x,y,color);
            }
        return;
        }
        requestAnimationFrame(update);
    };
    
    update();
}

function explode(x,y,color){
    var particle = document.createElement("DIV");
    particle.className = 'particle';
    document.body.appendChild(particle);
    var posx = x;
    var posy = y;
    particle.style.top = posy + 'px';
    particle.style.left = posx +'px';
    particle.style.background = color;
    var angle = Math.random() * Math.PI * 2;
    var speed = Math.floor(Math.random() *  (6-4) + 4 );
    setTimeout(()=> {particle.remove()}, 500);
    var vx = Math.cos(angle) * speed;
    var vy = Math.sin(angle) * speed;
    function update(){
        posx += vx;
        posy += vy;
        particle.style.top = posy + 'px';
        particle.style.left = posx +'px';
        
        requestAnimationFrame(update);
        
    }
    update();
}
        
    $('.button').click(function(){
        $('.frontCard').addClass('pageTurn');
        setTimeout(function(){
        $('.frontWrap').css("visibility","hidden")},2000);
});
    
    let second = $('.secondCard').children();
    $('.secondCard').click(function(){
        $('.secondCard').addClass('pageTurn');
        setTimeout(function(){
        second.css("visibility","hidden")},2000);
});
    let third = $('.thirdCard').children();
    $('.thirdCard').click(function(){
        $('.thirdCard').addClass('pageTurn');
        setTimeout(function(){
        third.css("visibility","hidden");
        $('.greetCard').css("display","none");    
        $("body").css("background","#111");},2000);
});
    
    let names = ["Mr. Gauhar","A"]
    setInterval(function(){
        $('#greet>p').text(names[Math.floor(Math.random()*4)])
    },1000);
});
