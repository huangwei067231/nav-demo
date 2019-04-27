<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        a{text-decoration: none;}
        kbd{border:1px solid red;
            text-transform: uppercase;
            display: inline-block;
            width: 50px;
            height: 40px;
            position: relative;
        }
        kbd > button{
            position: absolute;
            right: 0;
            bottom: 0;
            font-size: 5px;
            display: none;
        }
        kbd:hover > button{
            display: inline-block;

        }
        #mainx{
            display: inline-block;
            background:rgba(255, 255, 255, 0.2);
            border-radius: 10px;
        }
        #mainx > div:nth-child(2){
            margin-left: 1px;     
        }
        #mainx > div:nth-child(3){
            margin-left: -65px;
        }
        body{
            height: 100vh;
            background: #C5C5C5 url(./wallhaven.jpg) no-repeat center center scroll;
            background-size: cover;
        }
        main{
            text-align: center;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .key{
            color: #C5C5C5;
            background:linear-gradient(to bottom,#292929 0%,#111111 100%); 
            border:1px solid #373737;
            border-radius: 8px;
            box-shadow: 0 0 0 1px #1a1b1c,0 0 0 2px #1f2020,0 3px 0 2px #080808;
            font-size: 18px;
            font-family:Helvetica;
            position: relative;
        }
        .row{
            margin: 16px
        }
        .row .key{
            margin-left:7px;
            margin-right:7px;
        }
        .key img{
            width: 16px;
            height: 16px;
            position: absolute;
            left:4px;
            bottom: 2px;
        }
        .key .text{
            position: absolute;
            left: 4px;
            top: 4px;
        }
    </style>
</head>
<body>
    <header></header>
    <main>
       <div class="wrapper" id="mainx">
       </div>
   </main>
    <footer></footer>
    <script>
      var keys={
          0:['q','w','e','r','t','y','u','i','o','p'],
          1:['a','s','d','f','g','h','j','k','l'],
          2:['z','x','c','v','b','n','m'],
          length:3
      }
      var hash={
          'q':'qq.com','w':'weibo。com','e':'ele.me','r':'renren.com','i':'iqiyi.com',
          't':'tianmao.com','y':'youku.com','h':'huya.com','z':'zhihu.com','s': 'sogou.com', 
          'j':'jianshu.com','b':'baidu.com','d':'douyu.com','o':'opera.com','a': 'acfun.tv',
          'n':'www.51job.com', 'm':'www.mcdonalds.com.cn'
			}
      
      //取出localStorage中的'u'对应的hash
      var hashInLocalStorage=JSON.parse(localStorage.getItem('u') || 'null')
        if(hashInLocalStorage){
            hash=hashInLocalStorage
        }

            index=0
          while(index<keys['length']){
            div1=document.createElement('div');
            div1.className='row'
            mainx.appendChild(div1)
            row=keys[index]

            index2=0
          while(index2<row['length']){
             KBD=document.createElement('kbd')
             spen=document.createElement('spen')
             spen.textContent=row[index2]
             spen.className='text'
             KBD.appendChild(spen)
             KBD.className='key'
             buttonx=document.createElement('button')
             buttonx.textContent='编辑'
             buttonx.id=row[index2]
             img=document.createElement('img')
             if(hash[row[index2]]){
                img.src='http://'+hash[row[index2]]+'/favicon.ico'
             }else{
                img.src= 'http://baidu.com/favicon.ico'
             }
             img.onerror=function(error){
                error.target.src = 'http://baidu.com/favicon.ico'
             }
            
             buttonx.onclick=function(x){
                key= x.target.id
                b=prompt('请给我一个网址')
                hash[key]=b  //hash变更
                localStorage.setItem('u',JSON.stringify(hash))
             }
             KBD.appendChild(img)
             KBD.appendChild(buttonx)
             div1.appendChild(KBD)
             index2=index2+1
            }
            index=index+1
          }

         document.onkeypress=function(x){
               key=x['key']
               website=hash[key]
               //location.href='http://'+website
               window.open('http://'+website,'_blank')
          }
    </script>
</body>
</html>

