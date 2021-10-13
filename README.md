index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eyes Track</title>
    <style>
		*
{
    margin: 0;
    padding: 0;
}
body
{
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: radial-gradient(#f2761e,#ef4921);
}
.box
{
    display: flex;
}
.box .eye
{
    position: relative;
    width: 120px;
    height: 120px;
    display: block;
    background-color: #fff;
    margin: 0 20px;
    border-radius: 50%;
    box-shadow: 0 50px 45px rgba(0,0,0,0.2),
                inset 0 0 15px #f2761e,
                inset 0 0 15px #f2761e;
}
.box .eye::before
{
    content: '';
    position: absolute;
    top: 50%;
    left: 35px;
    transform: translate(-50%,-50%);
    width: 45%;
    height: 45%;
    border-radius: 50%;
    background:#000;
    border:5px solid #2196fe;
    box-sizing: border-box;
}
	</style>
</head>
<body>
    <div class="box">
        <div class="eye"></div>
        <div class="eye"></div>
    </div>
    <script>
        document.querySelector('body').addEventListener('mousemove',eyeball);

        function eyeball(){
            const eye = document.querySelectorAll('.eye');
            eye.forEach(function(eye){
                let x = (eye.getBoundingClientRect().left) + (eye.clientWidth / 2);
                let y = (eye.getBoundingClientRect().top) + (eye.clientHeight / 2);

                let radian = Math.atan2(event.pageX - x, event.pageY - y);
                let rotation = (radian * (180 / Math.PI)* -1)+270;
                eye.style.transform = "rotate("+rotation+"deg)"
            });
        }
    </script>
</body>
</html>
