# Протокол версии 5 (ЧЕРНОВИК)

!!! warning "Внимание"

    5-я версия протокола I2P-Bote находится в состоянии черновика.
    Могу происходить значительные изменения в документации.
    Это может приводить к некоторой непоследовательности в описании.

!!! note "Примечание"

    Все изменения, относящиеся к 5-ой версии протокола, промаркированы комментарием `[VER 5]`

!!! note "Примечание"

    На данный момент не все изменения 5-ой версии протокола реализованы на стороне **pboted**.  
    Был реализован только пакет *PeerListV5* для поддержки современных форматов адресов назначения в сети I2P.  
    Пакет *PeerListV4* поддерживается, старые узлы с **Java Bote** отвечают на запросы, не не инициируют их из-за повреждения форматированием всех I2P адресов к адресам DSA.

Полная поддержка 5-ой версии протокола I2P-Bote ожидается в **pboted** версии **1.0.0**.

Предложения по улучшению 5-ой версии протокола принимаются на обсуждение.
