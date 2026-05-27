**Questions to drive your writing, in order:**

**Big picture first:**

- Chapter 1 opened with the problem: epicardial leads are broadly labeled MRI-unsafe, and patients who most need MRI are being denied it. What did your work _actually show_ about whether that restriction is justified, at least for translational force?

		Yes temporal epicardial leads were generaly labeled MRI unsafe, i think that after 2000 their are more MR conditional. I think a good idea is to point the radiologist or technologist to the vendor for specifics. Well Vourien says it is not recommended. Medtronic website on leads (link)[https://www.medtronic.com/en-us/l/isw/surescan-mri-pacing-leads-indications-safety-warnings.html] have a cathegory "MRI SureScan™ leads" but they point to their manual and have a bunch of precautions like broken leads and say "no to abandoned leads"
		My work is a complementary study on the broader problem, it only addresses mechanical forces, with the translational force device (the pendulum) we constructed, one can go into the MRI with a given piece of the epicardial lead and test for defelction. A radiologist or resident radiologist can be trained to follow the protocol and check or a class on MRI safety can do a demostration on this device for leads. So two things i can see for applications: One researchers gather a wide set of most used epicardial lead by vendor and tries them under this device for a 3T scanner returns a list a radiologist can check to see if safe or not. Second having the resident radiologist see the lead move under the field creates this educational intuition on how much it can move when free. It is hard to say from a single result if the restriction is justified, given we only did a type of lead and tested it under a uncommon configuration (coil). I think in the general context yeah, better safe than sorry, particularly under those high fields where physics is not intuitive (we didn't expect it to be this high). However, the fact that the lead gave such small deflections and FR even in the coil form makes me think that a straight or slightly bent wire would yeield much less deflection. But more testing is needed.

- What is the one sentence summary of what this thesis accomplished that you could say to a radiologist who has never heard of ASTM F2052?

		The magnetic field of an MRI scanner (either 1.5T or 3T) is strong enough to make things that are considered non-magnetic behave in unexpected ways. The epicardial lead defecltion's or pull is miminal but not zero. What is the requiered force for a needle to push thorugh skin? the lead is experiencing 0.093 of its weight as force approx so i doubt it would be enough for it to push through. (im trying to make some feel to think of this) (this link)[https://www.scivisionpub.com/pdfs/left-ventricular-perforation-resistance-during-pleural-drainage-puncture-3991.pdf] says the _The needle of the PleurX™ system could perforate the heart with a force of as little as 1.3 N. the lead only does 0.118482mN in my trial... 4 orders of magnitude less? can we find a better analogy?

**On the methodology contribution:**

- You built three fixtures that didn't exist before in this configuration. What does it mean that they worked in a clinical 3T environment without interference? Is that itself a contribution worth naming?

		Yes, it is. The fact the fixtures work without interference is a good sign. It prompts us to follow up the work with more strict measuremnets or points of comparison. The first fixture, mapping the field, already existed and we made it following desing from ferreira etal. i think it is worth noting that even TG reports on checking B0 homogeinity suggest getting maps from vendors (this link)[https://aapm.onlinelibrary.wiley.com/doi/10.1002/mp.17351] and from what i read in radiology forums and mriquestoins on the topic, come in maps from vendors in documentation. Having an external way to measure should be encouraged. On the force fixture, my lit rev shows some smaller versions maybe more practical but i think ours have more presicion, explained in the section on the smallest force. and the torque uses a different method of what the standard suggests exploring its capacibilities should prove rewarding. Am i stating too many personal thoughts or believes here? No i dont think so but maybe restate it to be more polished. The fact that the fixtures worked as expected from the lab work is great. The only caveat is the torque one.
	
- What were the actual limits you hit — not failures, but honest boundaries of what this dataset can and cannot claim?

		Right, well first we only did a single type of temporal lead. Having a bigger sample would make this study stronger. Second we took an arbirary point as reference point to test, mapping and testing directly to highest point now known to be A6, as expected from literature, or at iso-center where the heart is closer to is more direcctly cliincally valuable that taht we did. The torque one has the most limitations, in my opinion starting from the circuit, the trim resistors may hinder the signal strenght. Dr Rutel noted it, my brother a mecatronic engenier noted it. From that making sure we have enough positive control samples of different sizes to be affected enough in terms of torque should be better. Am i missing things i think i am

**On the null torque result:**

- The clinical torque result was a null finding. Gastel is explicit: don't hide limitations, discuss what impact they have on conclusions. What are the _two or three most likely explanations_ for that null result, and what would you need to change to resolve it?

		Well the first thing to comes to mind is the size of the sample... we trim our 316L ss to weight as much as the epi lead for the translational experiment, then the torque experiment may be too small for it to see. Another thing is that maybe making the transfer arm lighter may help improve the overall function. you know less mass maybe easier on the bearings and easier on the sample to transfer to the sensor. In general smaller on some pieces could be better. I think before redisigning the whole thing better samples should be tested. I guess practically this part of the experiments come in the later part of a measuring session. having a dedicated session for torque could be worth thinking of so all this can be tested without rush.

**On your "accidental" geometry finding:**

- The coiled titanium deflected more than the straight titanium despite identical material. You noted this but didn't fully resolve it. Is this a limitation of your current dataset or the beginning of a hypothesis worth stating explicitly?

		a way to attach securely the epicardial lead to the basket was by thighten it coiled it around it. like a wire is around a card. That may have added some "layers" to how the force was applied to parts of the lead. the 316 ss was almost the same as the lead, in its straight form that was surprising. We tested the Ti straight and got very little, okay as expected, we also tested a coiled Ti and it showed more force. I think it is important to say that it also weighted 10 times more than the other samples and it deflected a about 2.3 times more than its straight counterpart so it might be weight. or lenght it was longer... there where more material to be affected that might be it. but without further tests i cant really tell.

**On the pre-2000 vs post-2000 lead distinction:**

- Vuorinen (2021) found that distinction mattered clinically. You tested a modern lead. What would it mean if an older lead with different material composition produced a different force ratio? Is this a gap you can honestly name?

		I cannot. if and older lead produced a higher ratio may mean that vendors are really improving composition of their products to be MRI safe. if it less tho... Vourinen fiding was a retrospective study on patients that already had an epi lead and needed and MR scan and they dont disclose how many of their sample had older leads. only one case, a transient elevation of the pacing threshold on someone that had that lead 29 yr with the study done in 2022 it was just safer for them to say modern post 2000 leads. Also isnt pacing threshold a current induced thing? not force...

**On future directions:**

- What is the _minimum_ next experiment that would let you say something more generalizable than a single lead configuration?

		go in again bring a bunch of epileads (different types, vendors, configs[straight up, straight sideways, curved, coiled up and sideways]) and control [ti and 316L up and sideways], map the field again... adjust the translational fixture for either iso or A6 keep torque for a different session. The session on translational is justified as we can help generalize the results. The torque may need more work in the bench, because of the circiut... but a session on the clinic is justified to bring more positive samples of sizes and measure more than zero. 316L is a good one.

- What would it take to turn this methodology into something a clinical physicist could run as a routine safety check?

		When encountered. the physisicst should have access to the field maps given by vendors. if possible known the field already or measure with ferreira like fixture or pointed for iso. Given the highest point found on studies test particular positions and configs for the particular lead a patient would be scanned with. Determine safety to this particular forces by ASTM or better (im thiniking of the potential damage to neighbor tissue, but i havent seen any docuemnt outline that) A physisict should also be testeing for RF-heat, gradient induced currents. As this test was only a piece of a much broader study on safety concenrns.

---

**Structural suggestion following Gastel's "inverted funnel" for discussions:**

1. Restate the core finding in plain language (2–3 sentences, not a list)
		
		The methodologies and fixtures presented on this study prove to be working in the MRI suite. The unipolar epicardial lead by MEDTRONIC had a FR = 0.092, 5.32deg, well below the ASTM threshold of FR=1, 45 deg. This result does not mean the lead is safe, as it has to be tested for heat and current induction.
1. Connect back to the literature gap you named in Chapter 1 — did you close it, partially close it, or reframe it?
		
		I think this work takes a step forward bridging this gap, the retrospective studies inform and motivate. This study proposes fixtures and methodologies to quantify exactly the forces we are dealing with. It succeeded in 2 out of the 3. Protocol developing is still possible but it seems to be a clear possibility as explained for the physicist question. it needs more work and the investigation on the heat and induction. the heat was studied by bright a previous student thats aboyewa et al work. so we can inform the methodology above by his work. i guess. I think in general we covered the scope objectives well. we deployed a workable methodology, that methodology is capable of measuring mN forces, we fall a little short on the protocol development or decision-support tools but the potential for educational practice is there. (i tried to provide it above with the comparison but is a small contribution and i cant generalize)
1. Honest scope statement — single configuration, single session, what generalizes and what doesn't
		
		It shows the method works, it shows we can measure with precision. and therefore we can move on and do more trials for general things. On the torque shows better sampling is critical and that circuit design is important to address. nothing more on the physics or safety
1. The two or three genuine implications (torque null result, geometry effect, methodology validated)
		
		the geometry effect is more like a assuption or observation on what we did. Tho if it really matters and the coil is multipling the effects then our results are far better that we think. the lead may be coiled a bit or tweaked but not 6 or 7 times on a tight 14mm radius. is worth checking and stating what a "loose" lead would look like. right on the other 2
1. Future directions as specific as you can make them — not "further study is needed" but "the next experiment should test X because Y"
		
		see the minimum next experiment.
1. One closing sentence that returns to why this matters for the patient population
		
		The findings of this study set a presedent on that the static magnetic field of an MRI scanner do affect epicardial leads in an extend that is 0.9% the safety treshold and if compared to force neded for tissue damage from medical tools around the epicardium is 4 orders of magnitud less. This study, the previous from aboyewa etal. and the continuous work on the topic can lead to the proper understading or rigor in methodology and documentation to give access those patients that needed it. with the numbers of cied implants growing each year the population that may need an MRI will continue to grow with it. Keeping the MR suite save is the driver.