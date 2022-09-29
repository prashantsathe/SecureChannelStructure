# SecureChannelStructure

source code hierarchy (use https://www.planttext.com/ to see the image)

```
@startuml

package com.android.javacard.SecureChannels {
    abstract FiraSecureChannel
    abstract FiraClientContext
    
    package "Scp Instance" <<Rectangle>> {
      class scp
      class Scp11Lib
      class Scp3Lib
      class Certificates
      class Crypto

      FiraSecureChannel <|-- "Only one Active session" scp
      FiraClientContext <|-- scp
      scp *-- Certificates
      scp *-- Scp11Lib
      scp *-- Scp3Lib
      scp *-- ScpConstant
      scp o-- Crypto
    }
    
    package "fiRa Instances" <<Rectangle>> {
      class FiraSC
      class FiraInitiator
      class FiraResponder
      class FiraContext

      FiraSecureChannel <|-- "1..20 Instances" FiraSC
      FiraClientContext <|-- FiraSC

      FiraSC *-- FiraInitiator
      FiraSC *-- FiraResponder
      FiraSC *-- FiraContext
      FiraSC *-- Scp3Lib
      FiraSC *-- Certificates
      FiraSC *-- FiraConstant
      FiraSC *-- FiraCommon
      FiraSC o-- Crypto
    }
}
@enduml

```
