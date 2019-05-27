<template>
   <div>
  		<keep-alive>
   			<router-view></router-view>	 
   		</keep-alive>
		<navBar></navBar>
   </div>
</template>

<script>
 import navBar from 'components/navBar'
export default {
   components:{
        navBar,
   }
}
</script>