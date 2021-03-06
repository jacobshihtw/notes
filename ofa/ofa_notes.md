OFA notes
===
1. [classes](#classes)
   1. [Graph/OSD](#class_osd)
   1. [Rect](#class_box)
   1. [Position](#class_box)
   1. [Box](#class_box)
   1. [Shape](#class_shape)
   1. [MovingObject](#class_moving_object)
   1. [MVConfig](#class_mvconfig)
1. [flow charts](#flow_charts)
   1. [object detection](#flow_object_detection)
   1. [process mv data](#flow_process_mv_data)
   1. [process puzzle](#flow_process_puzzle)
1. [note](#note)
   1. [compose the intersect or adjacent objects to one](#note_1)
1. [test cases](#test_cases)
   1. [no object](#test_1)
   1. [one object and one box](#test_2)
   1. [one object and two boxes](#test_3)
   1. [two objects with different motion vector](#test_4)
   1. [multiple objects](#test_5)
1. [special scenarios](#special_scenarios)
   1. [motion vectors differ in hands and feet of a walking human](#scenario_1)
   1. [overlapped objects moving apart](#scenario_2)
   1. [shadow effect](#scenario_3)

---
<a name="classes" />

## classes

---

<a name="class_osd" />

### Graph/OSD

![Graph/OSD](http://www.plantuml.com/plantuml/png/bP4x3i8m38RtdC8RHHIneue9YP610rGcDIKY95LYnBDtnsq1CLGy5bksFplvRJPi2PQhEMYBCK91uWEoyKwf2lKEIm8V2xWg05n73gZvmIu2Ljks032wFejr4V2O3FkokJMEaatm-_oKGklFAR1l8h7d_gP0cXCX13sciEs7j0dQqWCBM9X3x0UPJizf6-yuXMWk9CzBkccebPXENhEKB8ELSQKbzWvcivVOoB8YNPV4kN4IE4t94APDJqUyB-4FwHy4Vv7vixZkQjbjF6v_Mwl9uEtEWyaT)

---

<a name="class_box" />

### Rect/Position/Box

![Rect/Position/Box](http://www.plantuml.com/plantuml/png/VLHHRzf037xFhx2OrC0AL7kTAAgglMzQVq1qkHXoRNA7xfm5Ll7VPry8IQ4C2R0_sz_PFlkU0YbFJLqb2Hcg49xT_k4tQW9TgH0mG84iUKN6sII98Fny-G6h5RmOkwsGd8Nr6juJWFjtPYEZZrkap5XMhCRf3BvBXDWBhzhfh9UoobYSRhohi_qSulzX3kH4uz_3uEWveIcZR6xdK0u6RRoky6JogZ1D68o4-pvguopD8PY_oDGCpv9ZakoKVbDRXDpjO_fTSR5uKPd6M8Bz81u6iHt4iXCht52iZMLljkLP8RVhnTmHkRhNJCWaA7ER4H93Fq8gTtzmfETOkNQaOxsZmzY_U5KQBOqWpXDzuCgmwD766iAiDLH6XFlHT-2NaxB-smAtGnu9vrSzMm-iBu77nola4hY_11QN6JsVRWZWIsK2hUIErY1J4JeqNfhe7P7CNvmPcJtjU1BZjTvTjsXaZF6Vj-o6Lur-YoSZftWdatGogU9cbCTQxlCpwv6_rX52d8AkjAu3AVEdKWefNYnG4930RQ1kg55Lz9HFNrStnVqAXcL7HIL2ZNME7jBOl1IKHn1uvuA9AtvciaNS5pb47CxCUUNqMpZxjQNH9ITMCqD7nTNnmm0kV-KZRfoSWWdHENUDBTZzp2VBU3hoYWWv9scF38QCnEJR1Buk5Z2narWmm_5fMYx5p2l-a8vsF7r8aYUcaCVk7m00)

---

<a name="class_shape" />

### Shape

![Shape](http://www.plantuml.com/plantuml/png/ZLHDRzim3BtxLn0Oq3g8c-vSUBdiuzfYwJrGPJOLfaY6nAxDilptKb-nlGL13abCFb9wV7mEAT88_aNq258Bxz53X_pa12bhgYecuNxr3TeMLifiD98ri5p2lWAOxprneJniaDRAS60arZEu2nq1xvnugsVbQQsLmVhPsUtwlO7uksk0R8ZuUpSKEfHKSvRXjmPU1a0g9pLco8bElVe197mlNS_MK0DU_K4-cjEpwb1LlP2_nARC6mP8uwsECS2ddtmrXFjJg9Mdzi4gGqlemuzF-Kw9BHAw6Ct3_95pc5rQLWB2ELS9tOidJqv8EYGzkEQtLHs3JAgG2FKYw9k9pC_KVjTQzVwIogzHhmiA7vswzFO7gtSRDi6voYHf-_VcPXXiciupJ9E9xZHNc4spcKGrNU8F5jcwNQPMt3cN3WLXFLfCt703l4yec_poEGmHZpdJFVB3LJR4kEt07sC9uSaIsMto2kGJmfspkno1Y1pYQ8l_wveZht57iZzO1vZa-wSp4nfrKDahz_H9iz23feiyWtw3yreMTgmZWyLgS0hCxZeD7Xrr2YmUEW4o6lzl5ekiAh-wjzUJT_VwzWC0)

---

<a name="class_moving_object" />

### MovingObject

![MovingObject](http://www.plantuml.com/plantuml/png/bLPRRzCm57xFhpXQfR6jQoTUfrAX8I7nC87On6la9cvhIEp8ThiBbD_EERwaSPeWgDGsFfVFduy_7-UziKpRNLrbLjYAmxtQ2xdvlFhE2mj5nOo1akE_PbOecMKDAtwmJI_kPmOXziGCCBbNbFeDBKf3lVV6E_KCA_Ni1mzRrd0mzEiCqoxCHQ6aiT15EKUOIn-v5yYULV0xIGbEONB3QfxlNTOO4DmY4rNvb5Apfno9NP1vhqI9vaCskBwFZ21UmZ8JpWPgDygL7_g8GdDc-LzeT25yobh8yhyIYeep7TVVQ5LmO_BQfSOoUESiEflTwsl5dVM0NwaintfOgsg_EH1eNrw3LM40J890KamM7DGwuJ4FQOwwJw97OAauslIQsMABTfT67xj5BJIy46l1I_3SmNF7UKiG1bZvdHLSMb2wJHFIScqm39EUXDqwd8tOSqb2Ywn2VVnQwDc5-Ms2IfYM_aZjNABUILnEfLH3euRXj0dxbFDgjrvpJP4RBhbchhxFt3YMwQfHh6bodqtSBCzVrOqoBNktwC5oKE5YnTpK1CknbBJPHt5_SU1HptX2xrb3yJLhl8cLOsAy1c__YfPpqFXByaI8gt_IyHsHkXfL8CthbunFM7d2PtA3ND54XKEIhOwE9MXLCAAcEGWR16tQ90QIFpb0iOQ2IMGJzTlEe2GVLpc9YCw4tsExPTOd4fDsbZ56W_kIDD2mEsQhD1qY2yzzmqjiMMb7ci-lXjfNBmuMytcQY0512cTlpnoArmdQWs3wAHtaRn-KN8lDIOW7RH5xhg-ES7JUkMk2R3rJKfSHgCSlYcgo-3MRfV6ti6XBjimEsSsReQljpKsMXKrebxA01q7YixXjowNRaEbFR6PM58SDjtdiREuAYMaODFaK48hMubj3BdVrYbCdcpGeRM7efYLlfOeVkH6lLEl9NfHSvLmMgiGK--BkogcGmbztKvewmJkQMzHEP8jzj9tEu7rc6DcS8fi1P3E6V8Yb9ILG5IT-ttLGdHkwKIIetTsELUqqcwxFz9p6UV4j87Q_YvCk5G8wtN8ufkPw4wzkv7jEnzivZZsnbw4vlWFm0L-xRg_DnMFGqACxolX79sUg6hegb5xuAiRXCXs-UzSRfyDfEfnrgtw6RNtHFHBNeGqlpu2PSEPZh6zF2rg6TxlozhpTWnDGqawIlSVcHk-QVm00)

---

<a name="class_mvconfig" />

### MVConfig

![MVConfig](http://www.plantuml.com/plantuml/png/vLN1Rfmm4BtxAqQfr6oQqgZNQXL5ogbIUqhLApBsGAmrDhA7JRVf_dkD7H2xiDlbt0k2cVTc7ZCF_E29EsfhpHWfqWZ2cb9LhUEah06XkVVeGMAuIp766Yusl3g6lZ80NdXoN53YmTV7Y8WfWDlNFhrNHj7gvZZAfLo5cfuW19IftiC6Tn_XCBJbkiK9jKAQevud-NdI9VqawYbrWjAM7xzHgJJc3QVdgHg-nN-0PLitSMnx5Yvfnjz_lWrvlOQdmD98OHdtzyFGmu99YMv2kGh5kH6uke4l0p72tlMh4gDOqPObkjoqTO4kXHg7GldE1GcXhTZaNlt6zBnL4csEHbWPYBHhKlnslEzEo47bSMAeVu0UkeoZqrvzrf_guESw-DaE_dI7qV3Jq9vKtMZyWR-e7_huVHUxUe6N5plud6ylSEiIZm9a3hdCawFo3dUUchquHNWfVhA5RwfuBAl_VGDnBFt7lFwJPHEFXhonX51O8bl7gXCRnxiQ3NcWv_GDAqFeIYx2OM3BeKEn0ov2p0Sb4SQ1kWATfiFpuLD8ev6nzmcDQOCdzRqjU8asmRNkbGdh7Fh66XaYKBP6TB8YGwj2bDMnmk7F-Y6JziLaSFNvgY_EzkpkUlOSlBvZx26KwOxKlm00)

---

<a name="flow_charts" />

## flow charts

<a name="flow_object_detection" />

### object detection

![object detection](http://www.plantuml.com/plantuml/png/PP2zJiH038JxVGhhggI917INWYjeA90ew2EpQoMMzYVQTJO7Y7V72G4XqLcVFVQCBqKmonAyCNjbp9aZ2wFdTnHEiJSn2K7cSH83SDDLTfJ0JXWZUU3ewAhyjWjf6uTALbB-rx_hrebaeWoIO2G13ZWIE1Gq51riHunP9_O4ZKoPq0sxeViMk43pHgNLDUUdvyT1vI-XFgYqLpJh4E-dJtDEbag1KFV59_ZGleeEFeGwRBnf-s_kCgxmcfReE8vQN0zkqTl5eyQs52MZXpbnbB-gaEgcSPmrx_ucWCyVWvayOQ5VanhmI1PJkpqwpUQYKD_-1G00)

---

<a name="flow_process_mv_data" />

### process mv data

![process mv data](http://www.plantuml.com/plantuml/png/XLHDRwCm4BtxLpnrBo15_83aq9vwMwtKSwNACKDm5snaEv1arV_UiVaefAjT3WZFntipRyOy-I1TEBUD41r_wA2jmSDFssjp-dLy9nMUfGhMNOlEMKNUlxNzMoc3pF87_14fMuYXrWqXqnwX9aTeUyGOQ8FZkQh8FUPWPtObdmj0LyYM40zZ0sxaR1wppH85x5-O7uvVsMM7wmx33dL-I3vE8ZXzgaCw0ftrO_NIbF3wHfFTLX4MnyQgtqMo4GV4z7HOTTsTRxU62bcMOtDZ_lv4OKIm5pJQ1sJynIMYbK7Lh5FoJlqSfgnlvG4_C190MHEaDXuoOhQoOm0P6AxpIt1yrgH-OGqsERniQHFTsjH5Jt5SnOfrKxkEh9uxObaI80OTwWrGHFuxsYBSB4sbsJBZHo3m9gWwcLvDaZmnbkzIaM5InoiHo7c6fV8muyHzuB08KjcpAH-_RG9pDvutpDXygNMl74bMMSBGa9BZv5yDpo-AT3-kmrSJkfeRIB7pTipISlm_nyZbIlolkOsaIPeqxHrqu6FJuCYLboMLAzRrr8Oem8PcYfrWffGx6iQbInTrqC5JKyK4PNjoztVWxXPyY5aOVa-tEMejzlEr7tStOnd5HfIMt8aI-j8yAy6EHPTnpRWGQmWs_LCAyRLAFjXEV0ZnnARu7_e4)

---

<a name="flow_process_puzzle" />

### process puzzle

![process puzzle](http://www.plantuml.com/plantuml/png/TL9HReCm3FtFAQn-XMdg0JPDwmMcNM3Ib183hY11YQ5RfzvzJe09ElKhB_WzFp-JGsGJUEXQfNe1nEGTzC6N6EDdFrmkBSAFogGrOyV1Z1WYmj5_TQRV2UdSa90rHU060q9lA82leFDPCcB9Fi27Cyuc5RGK6RGWZCLh0QBJtm8Lm1sVZI8v0jnw9XOvo9HjJu2dDp-Igz-F9vda0Nm-uGKgSbPtusDI5S-PwZmZ1AeRpjTCMGITuRAHFibncstYfdZYQ-p9bEWO93CvJXbAHWjduYPBnMqoGsUJNyPKWPvzf4Vb1sUBn7Qh7DZAEhJpqqro_IKf0nf6oJB7-1y4PevCkUIHUPUQiHROBuMqxRco7b4mLMfbl9Sa-mv3ZVh-1dDzoPrC4foDRhOWQFwjKyQhsdwvAdcFla_dGIhoTdy1)

---

<a name="note" />

## note

<a name="note_1" />

### compose the intersect or adjacent objects to one

- one pass loop cannot find an exact object which may be split to several boxes.
- it should have the second loop to compose the intersect or adjacent boxes to one object.

![example](https://imgur.com/82tvyF6.png)

---

<a name="test_cases" />

## test cases

<a name="test_1" />

### no object

```
                             1 1 1
       1 2 3 4 4 5 6 7 8 8 9 0 1 2
   0 8 6 4 2 0 8 6 4 2 0 8 6 4 2 0
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 0| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 8| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
16| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
24| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
32| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
40| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
48| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
56| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
64| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
[expected result]
MovingObjects:  0
```

---

<a name="test_2" />

### one object and one box

```
                             1 1 1
       1 2 3 4 4 5 6 7 8 8 9 0 1 2
   0 8 6 4 2 0 8 6 4 2 0 8 6 4 2 0
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 0| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 8| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
16| | | | |0| |0| | |0| | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
24| | | |0|0| |0|0|0|0| | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
32| | | |0|0|0|0| | |0| | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
40| | | | |0| |0| |0|0| | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
48| | | | | | |0| | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
56| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
64| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
[expected result]
MovingObjects:  1
motion vector:  0x00ff 0xff01
bounding box:   24 16 56 40
```

---

<a name="test_3" />

### one object and two boxes

```
                             1 1 1
       1 2 3 4 4 5 6 7 8 8 9 0 1 2
   0 8 6 4 2 0 8 6 4 2 0 8 6 4 2 0
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 0| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 8| | | | | |0|0| |0|0|0| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
16| | | | |0| |0|0|0| |0| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
24| | | | |0| | | | | |0| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
32| | |0|0|0|0|0|0|0|0|0| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
40| | | | |0| | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
48| | | | |0| | | | |0|0|0| | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
56| | | | | | | | | |0|0|0| | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
64| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
[expected result]
MovingObjects:  1
motion vector:  0x00ff 0xff01
bounding box:   16 8 80 56
```

---

<a name="test_4" />

### two objects with different motion vector

```
                             1 1 1
       1 2 3 4 4 5 6 7 8 8 9 0 1 2
   0 8 6 4 2 0 8 6 4 2 0 8 6 4 2 0
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 0| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 8| | | | | |0|0| |0|0|0| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
16| | | | |0| |0|0|0| |0| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
24| | | | |0| | | | | |0| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
32| | |0|0|0|0|0|0|0|0|0| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
40| | | | |0| | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
48| | | | |0| | | | |1|1|1| | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
56| | | | | | | | | |1|1|1| | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
64| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
[expected result]
MovingObjects:  2
motion vector:  0x00ff 0xff01
bounding box:   16 8 72 48
motion vector:  0x0001 0xffff
bounding box:   72 48 24 16
```

---

<a name="test_5" />

### multiple objects

```
                             1 1 1
       1 2 3 4 4 5 6 7 8 8 9 0 1 2
   0 8 6 4 2 0 8 6 4 2 0 8 6 4 2 0
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 0| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
 8| | | | | | | | | | | |0|0|0|0|0|
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
16| | |1|1| | | | | | | |0|0|0|0|0|
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
24| | |1|1| |2|2|2| | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
32| | | | | |2|2|2| |3|3| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
40| | | | | | | | | |3|3| | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
48| | | | | | | | | |3|3| | | |4| |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
56| |5| | | | | | | |3|3| | |4|4| |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
64| | | | | | | | | | | | | | | | |
  +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
[expected result]
MovingObjects:  6
motion vector:  0x0000 0xffff
bounding box:   88 8 40 16
motion vector:  0x0001 0xffff
bounding box:   16 16 16 16
motion vector:  0x0002 0xffff
bounding box:   40 24 24 16
motion vector:  0x0003 0xffff
bounding box:   72 32 16 32
motion vector:  0x0004 0xffff
bounding box:   104 48 16 16
motion vector:  0x0005 0xffff
bounding box:   8 56 8 8
```

----
<a name="special_scenarios" />

## special scenarios

<a name="scenario_1" />

### motion vectors differ in hands and feet of a walking human

- consider a walking human, the motion vector of left hand may be positive where the right hand is negative or vice versa.
- how to group the adjacent blocks of different motion vectors to an object?

![scenario_1](https://imgur.com/yklONkL.png)

----

<a name="scenario_2" />

### overlapped objects moving apart

- is there way to distinguish two (or more) overlapped objects from MV data?
- if the motion vectors of the objects are slightly different, it might be grouped to an object when those are overlapped.

![scenario_2](https://imgur.com/Mhw9Cnp.gif)

----

<a name="scenario_3" />

### shadow effect

- in ideal conditions, two separate objects can be recognized easily.

![scenario_3_1](https://imgur.com/biHMqPy.png)

- if shadow of one overlaps with another, the separate objects might be grouped into one.

![scenario_3_2](https://imgur.com/PekWPyA.png)
