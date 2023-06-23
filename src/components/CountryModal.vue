<template>
  <div v-if="countryInfo"  class=" fixed top-28 w-2/3 md:w-2/3 sm:w-5/6 bg-white text-gray-700 shadow shadow-gray-300 rounded">
           <div class="flex justify-between border-b border-gray-400 ">
            <div class="p-5 ">
              <span class="text-lg md:text-lg sm:text-sm text-center font-bold"> {{ countryInfo.name.official }}'s' Infomation</span>
            </div>
            <div class="p-5">
              <button type="button" class="rounded bg-gray-200 px-3 py-2 hover:text-white hover:bg-gray-400 text-lg md:text-lg sm:text-sm" @click="$emit('btn-close')">Close</button>
            </div>
           </div>
           <div class="m-10">
            <div class="flex">
              <div class="w-2/6 mr-4" >
                <img v-if="countryInfo.flags.png || countryInfo.flags.alt" :src="countryInfo.flags.png" :alt="countryInfo.flags.alt" class="w-60 md:w-60 sm:w-44 h-32 md:h-32 sm:h-24 ring-1 ring-green-400 p-1"/>
                <div class="mt-2 text-sm font-normal">
                  <span class="font-bold pr-2">Population:</span>
                  <span v-if="countryInfo.population">{{  countryInfo.population }}</span>
                </div>
                <div v-if="countryInfo.capital[0]" class="mt-2 text-sm font-normal">
                  <span class="font-bold pr-2">Capital:</span>
                  <span>{{  countryInfo.capital[0] }}</span>
                </div>
                <div v-if="countryInfo.area" class="mt-2 text-sm font-normal">
                  <span class="font-bold pr-2">Area:</span>
                  <span>{{  countryInfo.area }}</span>
                </div>
                <div v-if="countryInfo.maps.googleMaps" class="mt-2 text-sm font-normal">
                  <span class="font-bold pr-2">Maps:</span>
                  <span class="text-green-400 underline">
                    <a :href="countryInfo.maps.googleMaps" target="_blank">Google Maps</a>
                  </span>
                </div>
              </div>
              <div class="w-4/6">
                <div class="text-lg font-bold mb-4 text-green-400">
                  <span>{{ countryInfo.name.official }}</span>
                </div>
                <div class="text-sm font-normal mb-2">
                  <span class="text-sm font-bold pr-2">Common Name:</span>
                  <span v-if="countryInfo.name.common">{{ countryInfo.name.common }}</span>
                </div>
                <div v-if="countryInfo.name.nativeName" class="text-sm font-normal mb-2">
                  <div v-if="countryInfo.name.nativeName.ara">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.ara.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.ara.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.eng">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.eng.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.eng.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.fra">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.fra.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.fra.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.spa">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.spa.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.spa.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.cat">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.cat.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.cat.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.cal">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.cal.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.cal.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.hye">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.hye.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.hye.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.div">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.div.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.div.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.mkd">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.mkd.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.mkd.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else-if="countryInfo.name.nativeName.srp">
                    <span class="font-bold pr-2">Native Name:</span>
                    <span>
                      {{ countryInfo.name.nativeName.srp.official }}
                      (Official),
                      {{ countryInfo.name.nativeName.srp.common }}
                      (Common)
                    </span>
                  </div>
                  <div v-else>
                    <span/>
                  </div>
                </div>
                <div v-else>
                  <span/>
                </div>
                <div v-if="countryInfo.altSpellings" class="text-sm md:text-sm sm:text-xs font-normal mb-2">
                  <span class=" font-bold pr-2">Alternative Name:</span>
                  <span class="pr-2" v-if="countryInfo.altSpellings[0]">{{ countryInfo.altSpellings[0] }},</span>
                  <span class="pr-2" v-if="countryInfo.altSpellings[1]">{{ countryInfo.altSpellings[1] }},</span>
                  <span class="pr-2" v-if="countryInfo.altSpellings[2]">{{ countryInfo.altSpellings[2] }},</span>
                  <span class="pr-2" v-if="countryInfo.altSpellings[3]">{{ countryInfo.altSpellings[3] }}</span>
                </div>
                <div v-if="countryInfo.currencies" class="text-sm md:text-sm sm:text-xs font-normal mb-2">
                  <span class=" font-bold pr-2">Currencies:</span>
                  <span>
                    {{ countryInfo.currencies }}
                  </span>
                </div>
                <div  class="text-sm md:text-sm sm:text-xs font-normal mb-2">
                  <span v-if="countryInfo.idd" class="capitalize text-sm md:text-sm sm:text-xs font-bold pr-2">Calling Code:</span>
                  <span>{{ countryInfo.idd.root }}</span>
                  <span v-if="countryInfo.idd.suffixes" >{{ countryInfo.idd.suffixes[0]}}</span>
                  <span v-else></span>
                </div>
                <div  class="text-sm md:text-sm sm:text-xs font-normal mb-2">
                  <span v-if="countryInfo.region" class="capitalize text-sm md:text-sm sm:text-xs font-bold pr-2">Region:</span>
                  <span>{{ countryInfo.region }}</span>
                </div>
                <div>
                  <div v-if="countryInfo.borders"  class="text-sm md:text-sm sm:text-xs font-normal mb-2">
                    <span  class="font-bold pr-2">Borders:</span>
                    <span v-if="countryInfo.borders[0]">{{ countryInfo.borders[0] }},</span>
                    <span v-if="countryInfo.borders[1]">{{ countryInfo.borders[1] }},</span>
                    <span v-if="countryInfo.borders[2]">{{ countryInfo.borders[2] }},</span>
                    <span v-if="countryInfo.borders[3]">{{ countryInfo.borders[3] }},</span>
                    <span v-if="countryInfo.borders[4]">{{ countryInfo.borders[4] }},</span>
                    <span v-if="countryInfo.borders[5]">{{ countryInfo.borders[5] }}</span>
                  </div>
                  <div v-else>
                    <span/>
                  </div>
                </div>
                <div v-if="countryInfo.timezones[0]"  class="text-sm md:text-sm sm:text-xs font-normal mb-2">
                    <span  class="font-bold pr-2">Timezones:</span>
                    <span>{{ countryInfo.timezones[0] }}</span>
                </div>
              </div>
            </div>
           </div>
           <div class="flex justify-center py-4 h-16 border-t border-gray-400">
            <span class="text-sm text-center pr-2">Copyright &copy; 
              <span class="text-green-400">Rest Countries API</span>
            </span>
           </div>
          </div>
</template>

<script> 
export default {
  name: 'Modal',
  props: {
    countryInfo: Object,
  }
}
</script>