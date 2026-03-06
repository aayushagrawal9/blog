---
title: "USB-C PD isn't just for charging — it can revolutionize our relationship with electricity"
description: "Why centralized DC power distribution via USB-C Power Delivery could eliminate adapters, slash conversion losses, and reshape residential electrical infrastructure."
date: 2025-06-21 00:00:00 +0000
categories: [Technology, Energy]
tags: [usb-c, power-delivery, energy-efficiency, dc-power, sustainability]
---

Picture this: You turn on your TV. Or you plug in your laptop to charge. Maybe your headphones too.

What's the first thing all of them need to do? It's converting the A/C current in your outlets to D/C through in-built or external wall adapters.

Matter of fact, think about how many non-heavy electronics (So water heaters, space heaters, washing and drying machines etc are out) are there in your modern home that run on A/C? Fans? Lights? The modern standard BLDC fans run on DC and so do those modern LED lights.

And every single one of them is drawing in A/C power and converting it to D/C with conversion efficiency of about 85% (Based on data for common electronics in June 2025). High end adapters could bring that up to roughly 95% but those probably cost more than your device. The conversion ratio is roughly the same for AC to DC or DC to AC at 230V. The math doesn't change too much for 120V.

But what if it didn't have to be this way? What if we could install a single converter right on the mains supply? Traditionally this has been problematic because different devices require different DC voltages while a AC line voltage can be converted to the required DC by the device.

## Enter USB-C Power Delivery

But USB-C PD changes that! A device could request for 5 Volts or 12, 24 or 48! Modern USB-C PD can support up to 240 Watts of power delivery, more than enough for current electronic devices. There is unfortunately an efficiency loss thanks to the extra layer, current USB-C PD devices can lose as much as 5%.

You might be asking what's the point? I've got a perfectly functional MacBook with a big adapter I'm plugging into the wall, my monitor's also got a nice big charging brick, an adapter going into the wall for my phone. Even my medical equipment like CPAP machines have charging bricks going into the walls.. oh wait. Not to mention these lower quality adapters all waste an average of 15% in conversion losses.

If you're a keen reader you could rebut me here and say so what? Even if I use an expensive DC adapter at a house-wide level [Perhaps multiple if you're got a very big house or office floor!] I'd still lose 5% converting to DC and an additional 5% when it goes through the Power Delivery adapter. Compound that and you get roughly 90.25% efficiency. Sure that sounds better than 85% for AC to DC at the device-level but does 5% justify the overhaul?

## It's not just about efficiency

What if it wasn't just 5% in cost savings however? Think about it. You are not simply eliminating 5% of electricity wastage but also the absolutely gigantic amount of equipment and components that go into those charging bricks and internal power supplies. Material that requires rare earth elements. A feasibility study from 2016 by J. P. Das, R. J. Fatema and M. S. Anower titled "Feasibility study of low voltage DC distribution system for residential buildings in Bangladesh and hybrid home appliance design for tropical climate" found that a typical US household was already using 35--55 individual AC to DC converters with a rare earth material usage of 60--105 grams (That's a lot!).

That same study found that material consumption in the context of each device/dependency's power supply could be reduced by as much as 40--60% while providing efficiency gains of 5--16%. But I disagree with the lower end of that range, this is from 2016 after all. We can do better in 2025.

I want to emphasize that this isn't just about a 5--15% efficiency gain. This is about:

- **Dramatically simplifying our electrical infrastructure.** Our outlets turn into standardized USB C outlets that work anywhere in the world and can supply up to 240 Watts (Per the latest USB C PD spec), more than enough for most devices including lighting and fans with BLDC motors.
- **Materials reduction:** Valuable rare earth metals in short & vulnerable supply and electrical waste parts of which are not easily recycled (How much of your electrical waste would you say are old chargers and cables?). And the economic and environmental cost of manufacturing, delivering and disposing of those bricks & equipment.
- **Two in One:** USB C provides the ability to both transmit data and power! If your plugs support it, a single cable can provide both internet and power to a device through technology that already exists & is inexpensive. Now imagine all the extra networking material we eliminate.
- And speaking of power transmission, **Power over Ethernet (PoE ++)** is capable of supplying 90 Watts power! Perhaps we can explore a combination of the two if USB C data transmission over long lengths is troublesome.
- **The economic benefit** to us is not just 5 or 10% efficiency gains but a massive reduction in the need for all the converters that directly factor into your equipment's cost. And manufacturers don't have to worry about balancing between cheaper converters to manage price and more expensive ones to protect the equipment. Every device gets high quality DC straight from the outlet.

## Safety

We're just getting started here. Here's another juicy part --- Safety:

- **USB-C PD already brings with it centralized protections** including over/under current, high temperature, ESD, VBUS etc. Things that can damage your equipment and potentially even start fires. That's a big, preventable economic hit.
- Even better is the fact that the **USB-C PD standard requires standardized quality control** for cable & connectors that significantly eliminates faulty cable design. Instead of each manufacturer designing their own cables and procuring/designing their own adapters we get a simple, high quality, inexpensive design where competition can lower prices without compromising on safety standards.
- **48V DC is safer for our body than 230/120V AC.** Don't get me wrong --- both require safe handling and can be lethal. But when it comes to bad or outright irresponsible use of electricity, as humans are prone to do, DC can save many lives. 48V DC is much safer than 230V or 120V AC and victims are not paralyzed the same way as A/C and can pull away. Granted, DC can still be lethal but if we can prevent a large chunk of (Dare I say most?) electrocutions while simultaneously saving money and the environment, why not?

So is that it? I'll admit, it's a compelling case. But you might be asking whether this is truly worth the effort and investment. Even though USB-C PD technology is cheap, the retrofit would be pricey. Not to mention manufacturers switching to USB-C power input [And likely still needing to provide separate USB-C adapters for those still on A/C only]

## Power Backups: Where the savings really add up

But I have another argument to sell you on the money angle --- Power Backups. If you live in an area prone to blackouts/brownouts or you use sensitive/high reliability equipment such as medical equipment you need power backups. Most setups usually go for batteries and inverters. But remember when I said on average the efficiency losses on backup are almost 15% one-way? Here's what your inverter's doing:

1. When charging the battery (A/C to D/C): **15% lost**
2. When the power goes out (D/C to A/C): **15% lost**
3. Your device/adapter again converting power (A/C to D/C): **15% lost**

Compounded? **38%!** When you are running on your backup power supply at least 40-ish percent is going down the drain! [Technically it's even higher since there's also an efficiency loss during charging and discharging which is also influenced by temperature, unfortunately those are inevitable/outside the scope of this article]

But if this was a USB-C PD device?

1. When charging the battery (A/C to D/C): **5% lost**
2. No step two and three.

**5% loss as compared to 38%.** In the context of electrical grids these are massive savings. You may notice that step one in the first scenario is shown to show a 15% loss but in the second only 5%. This is because of my assumption of a regular inexpensive inverter facing a 15% loss.

I should note that modern top of the line pure sine wave inverters are able to achieve up to 90% efficiency (Or slightly higher under ideal environments). But that's still the first two steps and you'd still be looking at 25%+ losses through the entire conversion chain.

## The converter already exists

You might say Aayush, all this is great and it's fantastic that we already have Power Delivery technology developed and inexpensive. But you know what's expensive? That fancy AC to DC converter at the centralized level. That converts with 95% efficiency. How expensive will that be? What about future improvements causing me to have to buy a new one?

This is also already solved. The converter already exists and is in mass production after a great deal of optimization --- **EV chargers!**

EV chargers are not only already sophisticated and successfully achieve 95%+ conversion with high loads but are designed and tested to be rugged and survive harsh environments, common faults and more. That's exactly what we need! Not only does the technology exist but it is already battle-tested and mass-produced, just waiting to be converted into a USB-C PD capable system. And whoever does it first will have a pretty sweet first movers advantage.

## Even more savings from safety improvements

You might say alright, at this point you are seeing the utility in this crazy idea. But I can save you even more money:

- If you're in a place that's used to brownouts or simply running sensitive equipment you probably have **A/C stabilizers** protecting your equipment. Modern stabilizers will often try to control spikes and when they can't they will safely turn off power and wait a little after it's own supply stabilizes --- preventing against potential swings right as it powers back on.
- Then there's the **GFCI angle**. GFCI protection devices do, among other things, cut off power RAPIDLY when the current leaving the hot wire does not match the current returning to neutral --- they are vital to prevent electrocution. They can also protect your equipment. Unfortunately they are very expensive and often only deployed in bathrooms and kitchens.
- But a centralized, well designed electronic device that's delivering power via USB-C PD? It can monitor the current going in and out and terminate an outlet, protecting your device. This is not a replacement for GFCI devices for high risk areas aimed at protecting us from electrocution.
- With standardized DC over USB-C PD you can safely **eliminate some of these protective equipment** such as stabilizers given the PD provider is sufficiently complex and can detect the same issues. You could even seamlessly switch to battery in brownouts and keep using your equipment instead of waiting on the stabilizer.

## So what have we eliminated?

- **The massive trough of adapters and extra cables** etc filling up our landfills. Objects that we pay for, objects that have both an economic and environmental cost. Objects that use up precious rare earth metals.
- **Inverters** that are currently heavily utilized for continued usage of devices that draw small amounts of power during blackouts --- Fans, chargers etc. Again objects that we pay for. That have to be replaced and maintained and carry potential safety issues.
- **Some redundant protective equipment** like stabilizers --- Safely replaced at a central level in your home/floor.
- **Travel adapters** --- Just like you can plug your phone charger anywhere in the world regardless of the the electrical standards in that region (Voltage, Frequency etc), you can now run almost anything that can run on USB-C PD which can provide upto 240 Watts. Even my TV doesn't need that much. And gone are the days of the various adapter shapes when you just need a USB C outlet to power any electronics you're travelling with.
- **Bonus:** PD, being a smart power negotiating protocol enables your device and your cable to only work with a reliable connection. If the outlet is faulty and unable to negotiate or provide what it negotiated your device will kill the connection.
- **Conversion loss:** Instead of a 15% ish loss when your device converts AC to DC you face a 5% loss from the DC coming through your main board. PD can add an extra 2--5% but given that PD is still relatively new I believe this number can be significantly minimized when economic pressure demands it.

It's not just a 5--10% savings in electricity but a massive array of components you currently pay for that are no longer necessary. Economies of scale that further crush the current electrical equipment cost. Significant simplification of both structural wiring and the design of electronics we are already using. A clear and measurable increase in electronics safety that has returns not just in medical costs but prematurely damaged equipment, manufacturers having to spend less time and resources on stable DC supply to their electronics and more.

Lastly, this is already happening, but only somewhat! Data centers have begun to standardize to 48V DC supply over AC and have seen significant benefits. But this concept is struggling to escape specific industrial sites and I believe the use of pre-existing USB-C PD and retrofitted EV chargers changes everything.

## Shortcomings

But there are shortcomings:

- **Transition** --- This will inevitably bring along a transition period since we can't just modify wiring all over our buildings. And we've invested in expensive heavy equipment that we expect to use for a long time and some of which doesn't even benefit significantly from any conversion. Water heaters don't need to convert to DC and your dryer probably won't find it worth the conversion loss either. We should probably keep A/C outlets for heavy equipment. This could even provide some extra safety separating away the high-requirement devices & their power from everyday devices that get their power over USB-C.
- **Cable length** --- Traditional USB-C is only capable of transmitting at full power up to two or three meters. Even if you install your converter at the center of your home you probably can't cover outlets up to the very edge. A potential solution might be a combination of PoE ++ (The latest standard for Power over Ethernet which can carry upto 90W) and USB-C along with new innovations, perhaps a backwards-compatible development in USB C to allow DC transmission over longer distances, something that's already possible and well understood upto moderate distances.
- **Arc faults** --- For all the benefits DC carries one very annoying problem i.e arc faults. When the hot and neutral wires (In DC terminology also called positive and negative) are too close (And do not have or have lost appropriate sheathing) they can create a short circuit through the air. It's low current but the problem is this low current rises rapidly as the air itself heats up into plasma which has very little resistance. Arc faults occur in both AC and DC setups but DC faults are known to be harder to extinguish. Devices that can detect Arc signatures and kill the power supply exist and are expensive but perhaps the functionality can be integrated into our central converter.
- **Regulation** --- Rewiring will be a tussle with regulatory codes. But given the immense public benefit of reducing load on the power supply municipalities might benefit from rolling out the red carpet. The economic benefits businesses receive & the resultant demand would also incentivize lobbying efforts.
- **Security** --- The number one downside might be security. One of its greatest strengths is also a weakness --- USB C can carry both power and data including the ability to connect to the internet. But given the fact that giants such as Apple are already pushing for USB C to charge laptops etc I assume they think it's safe. I don't know what they know, only that they have already staked their reputation on it. It's a safe assumption that Apple is aware of USB C charging ports directly in wall outlets are already proliferating. But can we trust all manufacturers to maintain a required safety standard? A cable that only carries power to a BLDC fan is harmless. A cable that can do both combined with a cheap IoT BLDC fan is trouble. However I think that for IoT specifically the recent trend is for hubs such as Apple TV, Google Home or Echo devices to serve as middlemen. They could simply reject non-compliant IoT devices or perhaps we can even integrate a smart home system directly into the power system, providing not just power delivery and internet but also cybersecurity backed by a major player. Or at the very least, selectively enabling only some devices to have network access through the DC supply device, perhaps an app that allows us to authorize internet access to devices requesting it after they have identified themselves & had their cryptographic certificates validated.

## Conclusion

That's it. I wanted to highlight this concept and emphasize the fact that the tech already exists, past limitations (Such as various DC devices requiring different voltages) are addressed by recent developments and the economic, ecological, cybersecurity (Assuming security integration into the power/data supply), standardization benefits are undeniable.

Do you see a flaw I missed? Let me know!

You can also connect with me on X: <a href="https://x.com/AgentAayush?ref_src=twsrc%5Etfw" class="twitter-follow-button" data-size="large" data-show-count="true">Follow @AgentAayush</a>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
