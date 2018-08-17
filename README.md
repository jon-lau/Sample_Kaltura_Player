# Sample_Kaltura_Player
This sample video player can be used to display Kaltura hosted videos while displaying complementary resources (i.e. presentations & handouts). The video player offers a video library interface to organize multiple videos into respective subsections which allows users to navigate to related videos with ease. 

## Specifying a Video Library
The Module/Data directory holds the specifications for the video library. 

1. Module/Data/Module/module_data.xml dictates the overall library and references the videos that are available in the top left menu. The video player library can hold multiple sessions that are built from multiple parts. This file consists of a list of sessions which have 'parts' which reference specific videos. The title in the top menu is specified here in the `name` field of each part.


### List of Sessions
 `<sessions>
  <session name="Session 1" path="Session1">
   <part name="Sample Videos 1" path="part01" title="Sample Videos 1"/>
   <part name="Sample Videos 2" path="part02" title="Sample Videos 2"/>
  </session>
 </sessions>`

2. Module/Data/Module/Session1/part.xml specifies what is displayed while a video is playing. The first video tag represents the main video that will be played. Videos are specified by the `id` field. (The video ID will need to be associated with the partnerID (wid) specified in the KalturaPlayer/js/control.js file when the HTML player is initialized.) Within the main video tag you are able to specify relatedvideos, presentation slides, cuepoints and resources that are available. 

### Related Videos Example
    `<relatedvideos>
        <relate id="0_crv76sa2" title="Ka'upu Fledgling" thumbnail="#" content="#"/>
        <relate id="0_yw1cd72x" title="Papahanaumokuakea Marine National Monument" thumbnail="#" content="#"/>
        <relate id="0_mpoq358l" title="Halemaumau Lava Lake" thumbnail="#" content="#"/>
    </relatedvideos>`

### Presentation Slides Example
    `<cuepoints>
        <cuepoint id="VID01" time="00:00:00" src="media/Slides/noslide.png"/>
    </cuepoints>`


### Resources Example
    `<resources>
      <resource id="1" name="Handout: Sample PDF" src="media/Handouts/samplePDF.pdf"/>
    </resources>`

The second section to the part.xml files contains the related videos references. The videos in this section are generally of the same group (i.e. if there are 3 parts to a section then the remaining parts will be placed here). These video tags will also allow you to specify presentation slides, cuepoints and resources that are available. 

