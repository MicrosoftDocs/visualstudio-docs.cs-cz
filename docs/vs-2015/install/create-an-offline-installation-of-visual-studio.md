---
title: Vytvoření offline instalace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a6a9707d517a8a43d9a9ca156a5f7291ecee9bee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81445061"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Vytvoření offline instalace sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio naleznete v tématu [vytvoření offline instalace sady Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) nebo [Vytvoření síťové instalace sady Visual Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

Tato stránka popisuje, jak nainstalovat Visual Studio 2015, když nejste připojeni k Internetu. Chcete-li však provést odpojenou instalaci, je třeba nejprve vytvořit rozložení offline instalace pomocí počítače, který je připojen k Internetu. Tady je postup.

> [!IMPORTANT]
> Pokud je v offline počítači spuštěný systém Windows 7 SP1 nebo Windows Server 2008 R2, přečtěte si prosím zvláštní pokyny v části [řešení potíží s offline instalací](#BKMK_tshoot) tohoto tématu.  *Před* instalací sady Visual Studio 2015 je nutné postupovat podle těchto pokynů.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a> Instalace pomocí vytvoření offline instalace

#### <a name="to-create-an-offline-installation-layout"></a>Vytvoření offline rozložení instalace

1. Vyberte edici sady Visual Studio, kterou chcete nainstalovat, ze stránky pro stažení  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) .

2. Po stažení instalačního programu do umístění v systému souborů spusťte příkaz " \<executable name> /layout".

     Například spusťte: `vs_enterprise.exe /layout D:\VisualStudio2015`

     Pomocí `/layout` přepínače můžete stáhnout skoro všechny instalační balíčky, nejen ty, které se vztahují k počítači pro stahování. Tento přístup vám poskytne soubory, které potřebujete ke spuštění tohoto instalačního programu kdekoli, a může být užitečné, pokud chcete nainstalovat součásti, které nebyly původně nainstalované.

3. Po spuštění tohoto příkazu se zobrazí dialogové okno, ve kterém můžete změnit složku, ve které chcete rozložení offline instalace umístit.   Potom klikněte na tlačítko **Stáhnout** .

     Po úspěšném stažení balíčku by se měla zobrazit zpráva, že **instalační program byl úspěšný. Všechny zadané součásti byly úspěšně získány.**

4. Vyhledejte složku, kterou jste zadali dříve. (Například vyhledat D:\VisualStudio2015.) Tato složka obsahuje všechno, co potřebujete ke zkopírování do sdíleného umístění nebo instalačního média.

    > [!CAUTION]
    > V současné době Android SDK nepodporuje prostředí offline instalace. Pokud nainstalujete Android SDK položky instalačního programu na počítač, který není připojen k Internetu, instalace může selhat. Další informace najdete v části řešení potíží s offline instalací v tomto tématu.

5. Spusťte instalaci z umístění souboru nebo z instalačního média.

## <a name="updating-an-offline-installation"></a>Aktualizace offline instalace
 Společnost Microsoft vydala několik aktualizací pro Visual Studio 2015. Chcete-li aktualizovat instalaci sady Visual Studio, stačí stáhnout požadovanou edici ze stránky ze stránky pro stažení  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) . Potom postupujte podle kroků uvedených v tomto tématu a vytvořte nové offline rozložení instalace a pak ho použijte k aktualizaci vaší kopie sady Visual Studio 2015.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a> Řešení potíží s offline instalací
 Při instalaci offline z offline instalační mezipaměti se může zobrazit upozornění, že není možné instalovat některé součásti a balíčky. Následující tabulka obsahuje možná řešení pro tyto scénáře.

| Součást nebo balíček | Řešení |
|-|-|
| Dotfuscator and Analytics Community Edition 5.19.1 (pro edice Community, Professional a Enterprise sady Visual Studio, jak je nainstalované v **systému Windows 7 SP1** a **Windows Server 2008 R2**) | Pokud je v offline počítači spuštěný **systém Windows 7 SP1** nebo **Windows Server 2008 R2**, je nutné před instalací sady Visual Studio 2015 provést následující kroky:<br /><br /> 1. Nakonfigurujte soubor nebo webový server tak, aby stahoval soubory CTL.<br /><br /> 2. přesměrujte adresu URL automatické aktualizace Microsoftu pro odpojené prostředí.<br /><br /> Další informace najdete na stránce [Konfigurace důvěryhodných kořenů a nepovolených certifikátů](https://technet.microsoft.com/library/dn265983.aspx) na webu Microsoft TechNet. |
| Instalace Android SDK (úroveň rozhraní API) | Abyste mohli instalovat balíčky Android SDK (API Level), musíte mít připojení k Internetu. Pokud používáte omezenou síť, musíte při instalaci sady Visual Studio zapnout přístup k následujícím adresám URL:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Další informace o tom, jak vyřešit možné problémy s nastavením proxy serveru, najdete v příspěvku na blogu k [instalaci sady Visual Studio 2015 (Android SDK instalaci) za](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) Blogový příspěvek. |
| Šablony rozšiřující položky sady Visual Studio<br /><br /> GitHub Extension for Visual Studio<br /><br /> Nástroje PowerShellu pro Visual Studio | Pokud při instalaci sady Visual Studio 2015 nemáte připojení k Internetu, můžete k vygenerování offline rozložení instalace použít speciální offline kanál. **Poznámka:**  Tento speciální kanál obsahuje nejnovější aktualizace sady Visual Studio 2015. <br /><br /> Pokud chcete vytvořit speciální offline kanál, spusťte následující příkaz:/layout *Drive:* \VisualStudio2015/overridefeeduri *URL-to-feed-XML* .<br /><br /> Například pro speciální offline kanál v angličtině pro jazyk Visual Studio 2015 Enterprise spusťte:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Úplný seznam adres URL, které můžete použít k vytvoření speciálního informačního kanálu offline v jazyce podle vašeho výběru, najdete v následující tabulce. |

 Použijte následující adresy URL k vytvoření speciálního informačního kanálu pro konkrétní jazyk, jak je popsáno v tabulce výše.

|       Jazyk        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| Čínština (zjednodušená)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Čínština (tradiční) | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Čeština         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Němčina         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Angličtina        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Španělština        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francouzština         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italština        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japonština        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Korejština         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polština         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugalština       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Ruština        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turečtina        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio](install-visual-studio-2015.md)