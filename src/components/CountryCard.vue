<template>
  <div @click="$emit('btn-click', country.name.common )" class="bg-white rounded m-4 p-4 shadow hover:bg-gray-100 hover:shadow-lg hover:shadow-gray-300">
   <div class="flex">
    <div v-if="country.flags" class="w-2/6 sm:pr-2">
      <img :src="country.flags.png" :alt="country.flags.alt" class="w-60 h-32 md:w-60 md:h-32 sm:w-40 sm:h-24  rounded p-1 ring-1 ring-green-400">
    </div>
    <div class="w-4/6 ">
      <div class="mb-2">
        <span class="text-lg md:text-lg sm:text-sm font-bold">{{ country.name.official }}</span>
      </div>
      <div v-if="country.name.nativeName">
        <div v-if="country.name.nativeName.ara">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.ara.official }}
            (Official) , 
            {{ country.name.nativeName.ara.common }}
            (Common)
          </span>
        </div>
        <div v-else-if="country.name.nativeName.eng">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.eng.official }}
            (Official) , 
            {{ country.name.nativeName.eng.common }}
            (Common)
          </span>
        </div>
        <div v-else-if="country.name.nativeName.spa">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.spa.official }}
            (Official) , 
            {{ country.name.nativeName.spa.common }}
            (Common)
          </span>
        </div>
        <div v-else-if="country.name.nativeName.fra">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.fra.official }}
            (Official) , 
            {{ country.name.nativeName.fra.common }}
            (Common)
          </span>
        </div>
        <div v-else-if="country.name.nativeName.cal">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.cal.official }}
            (Official) , 
            {{ country.name.nativeName.cal.common }}
            (Common)
          </span>
        </div>
        <div v-else-if="country.name.nativeName.srp">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.srp.official }}
            (Official) , 
            {{ country.name.nativeName.srp.common }}
            (Common)
          </span>
        </div>
        <div v-else-if="country.name.nativeName.cat">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.cat.official }}
            (Official) , 
            {{ country.name.nativeName.cat.common }}
            (Common)
          </span>
        </div>
        <div v-else-if="country.name.nativeName.hye">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.hye.official }}
            (Official) , 
            {{ country.name.nativeName.hye.common }}
            (Common)
          </span>
        </div>
        <div v-else-if="country.name.nativeName.div">
          <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Native Name: </span>
          <span class="text-sm md:text-sm sm:text-xs font-normal pr-2">
            {{ country.name.nativeName.div.official }}
            (Official) , 
            {{ country.name.nativeName.div.common }}
            (Common)
          </span>
        </div>
        <div v-else>
          <span></span>
        </div>
      </div>
      <div v-else>
          <span></span>
      </div>
      <div v-if="country.altSpellings">
        <span class="text-sm md:text-sm sm:text-xs font-bold pr-2">Alternative Name:</span>
        <span class="text-sm md:text-sm sm:text-xs font-normal ">
          <span class="pr-2">{{ country.altSpellings[0] }},</span>
          <span class="pr-2" v-if="country.altSpellings[1]">{{ country.altSpellings[1] }},</span>
          <span class="pr-2" v-if="country.altSpellings[2]">{{ country.altSpellings[2] }}</span>
        </span>
      </div>
      <div class="flex ">
        <div>
          <div v-if="country.idd" class="text-sm md:text-sm sm:text-xs font-normal pr-4">
            <span class="capitalize text-sm md:text-sm sm:text-xs font-bold pr-2">Calling Code:</span>
            <span>{{ country.idd.root }}</span>
            <span v-if="country.idd.suffixes" >{{ country.idd.suffixes[0]}}</span>
            <span v-else></span>
          </div>

          <div v-else class="text-sm md:text-sm sm:text-xs font-normal pr-4">
            <span class="capitalize text-sm md:text-sm sm:text-xs font-bold pr-2">Calling Code:</span>
            <span>N/A</span>
          </div>

        </div>
        <div class="text-sm md:text-sm sm:text-xs font-normal pr-4">
          <span class="font-bold pr-2">2 Characters Code:</span>
          <span class="text-green-400">{{ country.cca2 }}</span>
        </div>
        <div class="text-sm md:text-sm sm:text-xs font-normal">
          <span class="font-bold capitalize pr-2 "> 3 Characters Code:</span>
          <span class="text-red-400">{{ country.cca3 }}</span>
        </div>
        
      </div>
    </div>
   </div>
  </div>
</template>

<script>
export default {
  name: 'Country Card',
  props: {
    country: Object
  }
}
</script>