Usage:

##################################

import vapoursynth as vs
import CSMOD as cs

core = vs.get_core()

src = core.lsmas.LWLibavSource('xxx.mp4')
cs = cs.CSMOD(src)


cs.set_output()


##################################


Params refers here

https://www.nmm-hd.org/newbbs/viewtopic.php?f=7&t=781


Changelog:
		1. change "ss_hq[bool]" to int(0~2).
			#0 using non-ringing Spline64Resize when (ss_w*ss_h < 3.0625) otherwise using nnedi3 with pscrn=2.
			#1 using nnedi3 in super sampling, but "pscrn" always sets to "1" (much slower but better quality)
			#2 using nnedi3 in super sampling, but "pscrn" always sets to "2" (faster, in other words, depth will be dithered to 8bit when necessary)
		2. add "showmask[bool]" to output internal mask.
		3. add greyscale support.
		4. remove "ssoutc[bool]", output chroma will always be fixed when "ssout=True"
		5. internal greyscale process when "chroma=False" (10% Faster).
		6. custom "kernel", "filter_ss", "filter_nr" are available but a little different. See Py files for details.
		7. remove "deband" preset and related params. You can use custom "filter_nr" instead.
		8. change "secure[bool]" to float, controls Threshold to avoid banding & oil painting (or face wax) effect of sharpening, set 0 to disable it.	
