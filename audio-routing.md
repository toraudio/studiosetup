# Audio channel routing

```mermaid
graph TD;
classDef mixerclass fill:blue,stroke:white,stroke-width:2px;
classDef synthclass fill:purple,stroke:black,stroke-width:1px,color:black;
classDef soundclass fill:yellow,stroke:black,stroke-width:2px,color:black;
classDef fxclass fill:green,stroke:black,stroke-width:1px,color:black;
classDef daw fill:red,stroke:white,stroke-width:3px,color:white;
subgraph Sub-Mixing
B(MicroMonsta2):::synthclass --- slotm9((9L)):::mixerclass --> A(Yamaha MG10):::mixerclass;
B(MicroMonsta2) --- slotm10((10R)):::mixerclass --> A(Yamaha MG10);
C(Volca Keys):::synthclass --- slotm1((1)):::mixerclass --> A(Yamaha MG10);
D(Neutron):::synthclass --- fx2(multi):::fxclass --- slotm2((2)):::mixerclass --> A(Yamaha MG10);
E(Crave):::synthclass --- fx1(reverb):::fxclass --- slotm3((3)):::mixerclass --> A(Yamaha MG10);
F(Microphone) --- slotm4((4)):::mixerclass --> A(Yamaha MG10);
G(ext.sources) --- slotm7((7L)):::mixerclass --> A(Yamaha MG10);
G(ext.sources) --- slotm8((8R)):::mixerclass --> A(Yamaha MG10);
end
L{DAW}:::daw --- intern((USB internal routing)):::soundclass --> Z(AudioInterface UMC-22);
subgraph Main
A(Yamaha MG10) --- slot1((1L)):::soundclass --> Z(AudioInterface UMC-22):::soundclass;
A(Yamaha MG10) --- slot2((2R)):::soundclass --> Z(AudioInterface UMC-22);
H(Model Cycle):::synthclass --- slot7((7L)):::soundclass --> Z(AudioInterface UMC-22);
H(Model Cycle):::synthclass --- slot8((8R)):::soundclass --> Z(AudioInterface UMC-22);
I(MicroFreak):::synthclass --- slot6((6)):::soundclass --> Z(AudioInterface UMC-22);
J{free} --- slot5((5)):::soundclass --> Z(AudioInterface UMC-22);
K(Blackbox):::synthclass --- fx3(TResonator-L):::fxclass --- slot3((3L)):::soundclass --> Z(AudioInterface UMC-22);
K(Blackbox):::synthclass --- fx4(TResonator-R):::fxclass --- slot4((4R)):::soundclass --> Z(AudioInterface UMC-22);
end
subgraph Monitoring
Z(AudioInterface UMC-22) --> mon1((Rokit5 L));
Z(AudioInterface UMC-22) --> mon2((Rokit5 R));
end
``` 
