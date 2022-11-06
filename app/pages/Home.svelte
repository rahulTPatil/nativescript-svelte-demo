<page>
    <actionBar title="NativeFlix - Demo">
    <actionItem
		ios.systemIcon="9" ios.position="left"
		android.systemIcon="ic_menu_share" android.position="actionBar" />
    </actionBar>
    <stackLayout height="100%">
    <listView height="100%" items="{flicks}" on:itemTap="{onFlickTap}">
      <Template let:item>
         <gridLayout
          height="280"
          borderRadius="10"
          class="bg-secondary"
          rows="*, auto, auto"
          columns="*"
          margin="5 10 5 5"
          padding="0"
        >
          <image row="0" margin="0" stretch="aspectFill" src="https://hatrabbits.com/wp-content/uploads/2017/01/random-word-1.jpg" />
          <label
            row="1"
            margin="10 10 0 10"
            fontWeight="700"
            class="text-primary"
            fontSize="18"
            text="{item.title}"
          />
          <label
            row="2"
            margin="0 10 10 10"
            class="text-secondary"
            fontSize="14"
            textWrap="true"
            text="{item.description}"
          />
        </gridLayout>
      </Template>
    </listView>
    <segmentedBar>
	<segmentedBarItem title="First" />
	<segmentedBarItem title="Second" />
	<segmentedBarItem title="Third" />
</segmentedBar>
  </stackLayout>
</page>

<script lang="ts">
import { Template } from 'svelte-native/components'
import { navigate } from 'svelte-native'
import { FlickService } from '../services/flickService'
import Details from './Details.svelte'

let flicks = FlickService.getInstance().getFlicks()

function onFlickTap(event) {
    navigate({
      page: Details,
      props: { flickId: flicks[event.index].id }
    })
  }
</script>

<style>
    /* .info {
        font-size: 20;
    } */
</style>
