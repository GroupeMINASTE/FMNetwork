# FMNetwork

FMobile Developer Pack v5. The power of FMobile's latest engine, FMNetwork, in a simple Swift Package.

## Installation

Add `https://github.com/GroupeMINASTE/FMNetwork.swift.git` to your Swift Package configuration (or using the Xcode menu: `File` > `Swift Packages` > `Add Package Dependency`)

## Usage

```swift
// Import the package
import CoreTelephony
import FMNetwork

// Create a variable and intitialize FMNetwork with the SIM card type you want.
// You can use .current, .sim, or .esim.
// Keep in mind that if you use .current, the SIM card type that will be returned in the card.type property is very likely to change to 
let current = FMNetwork(.current)
let sim = FMNetwork(.sim)
let esim = FMNetwork(.esim)

// Then access the properies you want.
// The FMNetwork class is composed of two properties : card and network, giving you data about the SIM card itself and its connected network. For example:
if current.card.mcc == current.network.mcc {
    print("The card is in its home country!")
}

// To access the full documentation, you can use the Quick Help feature in Xcode. Simply Command + click on any item of FMNetwork you wrote (for example the first mcc), and click on Show Quick Help to view the entire documentation for that part of the code.
```


## Public structure of the FMNetwork class

FMNetwork: (contains every data about a SIM card and its connected network)
  * card: FMNetworkSIMData (contains every data about a SIM card)
    * active: Bool (returns true if the SIM card is inserted and in use)
    * name: String (returns the name of the SIM card carrier, "Carrier" by default)
    * mcc: String (returns the Mobile Country Code (MCC) of the SIM card carrier, "---" by default)
    * mnc: String (returns the Mobile Network Code (MNC) of the SIM card carrier, "--" by default)
    * land: String (returns the uppercased 2-digit ISO country code* of the SIM card carrier, "--" by default)
    * type: FMNetworkType (.sim, .esim or .current)
* network: FMNetworkData (contains every data about the connected network of a SIM card)
    * name: String (returns the name of the connected network, "Carrier" by default)
    * mcc: String (returns the Mobile Country Code (MCC) of the connected network, "---" by default)
    * mnc: String (returns the Mobile Network Code (MNC) of the connected network, "--" by default)
    * land: String (returns the uppercased 2-digit ISO country code* of the connected network, "--" by default)
    * connected: String (Core Telephony [CTRadioAccessTechnology](https://developer.apple.com/documentation/coretelephony/cttelephonynetworkinfo/radio_access_technology_constants) constant, "" by default)
* fmobile: FMobileService? (contains complementary OTA data about the SIM card carrier, optional)
  * mcc: String? (returns the declared Mobile Country Code (MCC) of the SIM card carrier, nil by default)
  * mnc: String? (returns the declared Mobile Network Code (MNC) of the SIM card carrier, nil by default)
  * stms: Double? (returns the declared max speed of the national roaming network, 5000/nil by default)
  * hp: String? (returns the declared widest protocol for the home network, CTRadioAccessTechnologyWCDMA/nil by default)
  * nrp: String? (returns the declared widest protocol for the national roaming network, CTRadioAccessTechnologyHSDPA/nil by default)
  * land: String? (returns the declared 2-digit ISO country code* of the SIM card carrier, nil by default)
  * itiname: String? (returns the declared national roaming network name, homename/nil by default)
  * homename: String? (returns the declared home network name, nil by default)
  * itimnc: String? (returns the declared Mobile Netowk Code (MNC) of thenational roaming network, "99"/nil by default)
  * nrfemto: Bool? (returns the declared Femtocell activation status on the same radio technology as nrp, false/nil by default)
  * out2G: Bool? (returns the declared lack of 2G network for the home network, false/nil by default)
  * setupDone: Bool? (returns the declared FMobile setup done property, true/nil by default)
  * minimalSetup: Bool? (returns the declared FMobile minimal setup property, true/nil by default)
  * disableFMobileCore: Bool? (returns the declared FMobile national roaming core disability status, true/nil by default)
  * countriesData: [String]? (returns the declared ISO country codes included for data only at no charge, nil by default)
  * countriesVoice: [String]? (returns the declared ISO country codes included for voice only at no charge, nil by default)
  * countriesVData: [String]? (returns the declared ISO country codes included for voice and data only at no charge, nil by default)
  * carrierServices: [[String]]?  (returns the declared Carrier Services available to be displayed and used inside apps, nil by default)
  * roamLTE: Bool? (returns the declared 4G LTE national roaming status, nil by default)
  * roam5G: Bool? (returns the declared 5G national roaming status, nil by default)

*There is an exception for International carriers. They might return the non-standardised 2-digits code "WD", standing for World.

### To access the full documentation, you can use the Quick Help feature in Xcode. Simply Command + click on any property of the FMNetwork item you wrote, and click on Show Quick Help to view the entire documentation for that code.

## Examples

### Coming soon.

## Donations

If you are feeling generous and want to give a little something to the developer, you can do that [here](https://paypal.me/PlugNPay). It's completely optionnal.

You can also donate to the non-profit organisation directly, to help us finance our bigger projects [here](https://www.helloasso.com/associations/groupe-minaste/formulaires/1).

