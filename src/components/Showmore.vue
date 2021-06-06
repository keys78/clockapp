<template>
    <div>

        <div id="mySidenav" class="sidenav">
            <a href="javascript:void(0)" class="closebtn" @click="closeNav">&times;</a>
            <a href="#">About</a>
            <a href="#">Services</a>
            <a href="#">Clients</a>
            <a href="#">Contact</a>
        </div>

            <div id="main">
            <h2>Sidenav Push Example</h2>
            <span style="font-size:30px;cursor:pointer" @click="openNav">&#9776; open</span>
            <p>Click on the element below to open the side navigation menu, and push this content to the right.</p>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos, quibusdam ipsam. Voluptatem accusantium ratione, harum sequi a soluta nemo consequuntur neque possimus ipsam architecto itaque libero amet doloremque aliquid nobis tenetur! Nisi quidem quo earum amet eum, enim obcaecati labore exercitationem quae nam dolore nostrum unde ducimus consequatur omnis, qui id quasi? Voluptatem placeat minus dignissimos soluta repudiandae nesciunt, praesentium possimus inventore, quidem ab eveniet eos earum adipisci quam vitae laboriosam perspiciatis in quo ea! Quidem excepturi minima ea reiciendis voluptas sapiente in repellat minus eaque aspernatur. Distinctio voluptatem nisi qui? Eveniet minus repellat magni eum, tempore culpa excepturi animi, placeat corrupti vitae ullam ipsum ratione obcaecati odit earum at quo quam, ea nemo. Quaerat dolorem exercitationem minus soluta possimus esse dolore repudiandae molestias ullam ad, dolor eaque laborum architecto hic. Impedit veniam quaerat numquam a illo facere, reiciendis tempora magni repellat commodi suscipit laudantium nisi sit. Soluta laudantium ullam facere nemo assumenda perferendis in distinctio harum voluptatum ipsum reprehenderit, iusto, obcaecati nihil nisi ut magnam maxime quae beatae voluptas debitis minima reiciendis quidem vitae. Quam vel illum omnis minus, quis ut impedit odio quaerat quasi, odit ipsum nihil asperiores totam porro perferendis. Iusto officia vel quibusdam ducimus ut suscipit incidunt magnam sapiente sed impedit numquam consequuntur, cumque expedita totam fugit cupiditate laborum rem repellat voluptatum, eos harum, ea minima! Perspiciatis odit molestias maiores placeat natus alias tempore numquam exercitationem aperiam. Aut quam animi quos, ea cupiditate error facilis a suscipit distinctio dignissimos harum sapiente illum iste veniam, placeat alias! Deleniti consequatur delectus necessitatibus! Amet ipsum voluptatibus dolorum optio laborum. Corporis modi quaerat blanditiis dolor autem quibusdam placeat. Fugiat labore molestias numquam rerum vero quaerat nihil ab nemo sint sapiente alias, culpa earum a quisquam rem porro perspiciatis dicta ad, accusantium officiis est. Deleniti rem nam porro a minus placeat, aut dolores libero consequatur perferendis est sapiente? Dignissimos inventore ipsum quae quisquam fugit distinctio corrupti libero eum possimus voluptatem architecto vero cupiditate quos at asperiores, hic non sint nostrum recusandae vel corporis nam autem. Cum maxime, atque recusandae debitis eaque id deserunt odio et asperiores sed, ab ex non fugit nulla dolore quo nemo. Labore ullam culpa quaerat similique cupiditate tenetur facere possimus iure nesciunt sunt ratione illum nam minima aliquam atque, quasi iusto soluta magnam commodi? Iure molestias consectetur temporibus praesentium ut dolor vitae in. Inventore iure dolor numquam harum, autem qui vitae ipsum. Repellendus sint alias sunt, voluptates quos accusantium consectetur, distinctio quam, fugiat eos sequi. Commodi error hic reprehenderit asperiores incidunt eius omnis doloremque? Quasi molestiae, non deleniti perspiciatis doloremque laboriosam reprehenderit quia possimus, incidunt a voluptate, dignissimos cupiditate id cumque aspernatur pariatur. Asperiores accusantium dolor corporis in, doloribus velit ex sequi delectus aliquam id animi dolores aut dolorum a necessitatibus earum recusandae laborum aperiam, saepe blanditiis. Ex aut voluptatum iusto voluptatibus rem facere labore iure ratione repellat accusantium, doloremque eveniet, distinctio aspernatur fuga placeat laboriosam unde officiis eius facilis? Repellendus aliquam quis quia nobis illum mollitia debitis, suscipit facere. Tenetur iusto officia ducimus omnis, eius eaque!</p>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit\tum. Ullam distincti</p>
            </div>

            <!-- <div class="absolute bottom-0 left-0 h-2/4 bg-gray-200 w-full">
                <p>we are here</p>
            </div> -->

    </div>
</template>

<script>
    
export default {
    name: 'Shoremore',
    
    data() {
        return {

        }
    },

    methods: {
        
        openNav() {
        document.getElementById("mySidenav").style.height = "600px";
        document.getElementById("main").style.marginBottom = "600px";
        },

        closeNav() {
        document.getElementById("mySidenav").style.height = "0";
        document.getElementById("main").style.marginBottom= "0";
        }



    }







    
}

</script>

<style>

.sidenav {
  width:100vw;
  height: 0;
  position: fixed;
  bottom: 0;
  z-index: 1;
  background-color: #111;
  overflow-x: hidden;
  transition: 0.5s;
}

.sidenav a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
  transition: 0.3s;
}

.sidenav a:hover {
  color: #f1f1f1;
}

.sidenav .closebtn {
  position: absolute;
  bottom: 0;
  right: 25px;
  font-size: 36px;
  margin-left: 50px;
}

#main {
  transition: margin-left .5s;
  padding: 16px;
}

@media screen and (max-height: 450px) {
  .sidenav {padding-top: 15px;}
  .sidenav a {font-size: 18px;}
}

</style>