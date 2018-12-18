---
title: Vytvořit Offline instalaci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 0ac8f1c1d631e4d5f682fea5e1841e3914241d14
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055235"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Vytvoření Offline instalace sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci pro sadu Visual Studio 2017 najdete v tématu [instalace sady Visual Studio 2017 v pomalé nebo nespolehlivé síti prostředí](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network), nebo [vytvoření síťové instalace sady Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio) a [Speciální aspekty pro prostředí offline instalace sady Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment).

Tato stránka popisuje postup instalace sady Visual Studio 2015, když nejsou připojeni k Internetu. Však "odpojené" instalace, musíte nejprve vytvoříte rozložení pro offline instalaci pomocí počítač, který je připojený k Internetu. Tady je postup.

> [!IMPORTANT]
>  Pokud je offline počítač se systémem Windows 7 SP1 nebo Windows Server 2008 R2, naleznete zvláštní pokyny v [odstraňování potíží s offline instalací](#BKMK_tshoot) části tohoto tématu.  Musí postupovat podle těchto pokynů *před* nainstalujete Visual Studio 2015.

##  <a name="BKMK_Offline"></a> Instalace vytvořením offline instalace

#### <a name="to-create-an-offline-installation-layout"></a>Chcete-li vytvářet rozložení offline instalaci

1.  Zvolte edici sady Visual Studio, kterou chcete nainstalovat z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) stránce pro stažení.

2.  Po stažení instalačního programu do umístění v systému souborů spusťte "\<název spustitelného souboru >/layout".

     Například spusťte: `vs_enterprise.exe /layout D:\VisualStudio2015`

     S použitím `/layout` přepínače, můžete stáhnout téměř všechny instalační balíčky, nejen ty, které se vztahují k počítači ke stažení. Tento přístup vám dává soubory, které je potřeba spustit tento instalační program kdekoli a může být užitečné, pokud chcete nainstalovat součásti, které původně nebyly nainstalovány.

3.  Po spuštění tohoto příkazu se zobrazí dialogové okno, které je možné změnit složku offline instalace rozložení uložená.   Klikněte **Stáhnout** tlačítko.

     Je-li stažení balíčku úspěšné, zobrazí se zpráva, že **instalace úspěšná! Všechny zadané součásti byly úspěšně získány.**

4.  Vyhledejte složku, kterou jste zadali dříve. (Vyhledejte například D:\VisualStudio2015.) Tato složka obsahuje všechno, co potřebujete zkopírovat do sdíleného umístění nebo instalační médium.

    > [!CAUTION]
    >  Sady Android SDK v současné době nepodporuje prostředí offline instalace. Pokud nainstalujete na počítač, který není připojený k Internetu položky instalace sady Android SDK, instalace se nemusí podařit. Další informace najdete v části "Řešení potíží s offline instalace" v tomto tématu.

5.  Spusťte instalaci z umístění souboru nebo z instalačního média.

## <a name="updating-an-offline-installation"></a>Aktualizace offline instalace
 Společnost Microsoft vydala několik aktualizací pro sadu Visual Studio 2015. K aktualizaci instalace Visual Studio, jednoduše stáhnout edice, ze z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) stránce pro stažení. Potom postupujte podle kroků uvedených v tomto tématu můžete vytvořit nové rozložení pro offline instalaci a pak ji použijete k aktualizaci kopie sady Visual Studio 2015.

##  <a name="BKMK_tshoot"></a> Řešení potíží s offline instalace
 Při offline instalaci z offline instalaci mezipaměti, může se zobrazit zprávy s upozorněním nebude moct instalaci některých komponent a balíčků. Následující tabulka obsahuje možné řešení pro tyto scénáře.


|                                                                                       Součásti nebo balíčku                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                   Řešení                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nástroj Dotfuscator a Analytics Community Edition 5.19.1 (pro edice Community, Professional a Enterprise sady Visual Studio, jako nainstalovanou v **Windows 7 SP1** a **systému Windows Server 2008 R2**) |                                                                                                                                       Pokud je offline počítač spuštěný **Windows 7 SP1** nebo **systému Windows Server 2008 R2**, musíte provést následující kroky před instalací sady Visual Studio 2015:<br /><br /> 1.  Nakonfigurujte souborový nebo webový server pro stahování seznamů CTL.<br /><br /> 2.    Přesměrujte Microsoft URL adresy automatických aktualizací pro odpojené prostředí.<br /><br /> Další informace najdete v tématu [konfigurovat Důvěryhodné kořeny a zakázané certifikáty](https://technet.microsoft.com/library/dn265983.aspx) stránky na webu Microsoft TechNet.                                                                                                                                       |
|                                                                                  Instalace sady Android SDK (úroveň rozhraní API)                                                                                   |                                                                        Musíte mít internetové připojení k instalaci balíčků sady Android SDK (úroveň rozhraní API). Pokud jste v síti s omezeným přístupem, musí umožňovat přístup k následujícím adresám URL, když instalujete Visual Studio:<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Další informace o tom, jak vyřešit možné problémy s nastavením proxy serveru, najdete v článku [selháním (instalace sady Android SDK) za proxy serverem instalace sady Visual Studio 2015](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) blogový příspěvek.                                                                         |
|                             Šablony pro rozšiřující položky sady Visual Studio<br /><br /> Rozšíření GitHub pro Visual Studio<br /><br /> Nástroje Powershellu pro Visual Studio                             | Pokud nemáte připojení k Internetu při instalaci sady Visual Studio 2015, můžete použít speciální offline kanál ke generování rozložení pro offline instalaci. **Poznámka:** tento speciální kanál obsahuje nejnovější aktualizace pro sadu Visual Studio 2015. <br /><br /> Vytvořte offline kanál speciální, spusťte následující příkaz: / Layout *jednotka:* \VisualStudio2015 /overridefeeduri *adresu URL pro informační kanál xml*<br /><br /> Například pro anglickou speciální offline kanál sady Visual Studio 2015 Enterprise, spusťte tento příkaz:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Úplný seznam adres URL, které můžete použít k vytvoření speciální offline kanálu v jazyce podle vašeho výběru najdete v následující tabulce. |

 Pomocí následující adresy URL vytvoření specifické pro jazyk speciální offline informačního kanálu, jak je popsáno v předchozí tabulce.


|       Jazyk        |                            Adresa URL                            |
|-----------------------|-----------------------------------------------------------|
| Čínština (zjednodušená)  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Čínština (tradiční) | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Čeština         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Němčina         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Angličtina        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Španělština        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francouzština         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italština        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japonština        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Korejština         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polština         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugalština       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Ruština        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turečtina        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Viz také
 [Instalace sady Visual Studio]()