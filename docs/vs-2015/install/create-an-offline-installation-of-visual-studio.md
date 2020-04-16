---
title: Vytvoření offline instalace | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445061"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Vytvoření offline instalace sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete [v tématu Vytvoření offline instalace sady Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) nebo Vytvoření síťové instalace sady Visual [Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

Tato stránka popisuje, jak nainstalovat Visual Studio 2015, když nejste připojeni k Internetu. Chcete-li však provést "odpojenou" instalaci, musíte nejprve vytvořit rozložení instalace offline pomocí počítače připojeného k Internetu. Zde je návod, jak to udělat.

> [!IMPORTANT]
> Pokud je v počítači s offline systémem Windows 7 SP1 nebo Windows Server 2008 R2 spuštěn, přečtěte si zvláštní pokyny v části [Poradce při potížích s offline instalací](#BKMK_tshoot) tohoto tématu.  Před instalací sady Visual Studio 2015 *je* nutné postupovat podle těchto pokynů.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a>Instalace vytvořením offline instalace

#### <a name="to-create-an-offline-installation-layout"></a>Vytvoření rozložení instalace offline

1. Zvolte edici Sady Visual Studio, kterou chcete nainstalovat, na stránce [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) stahování.

2. Po stažení instalačního programu do umístění v systému souborů spusťte spustit název spustitelný\<soubor> /layout.

     Spustit například:`vs_enterprise.exe /layout D:\VisualStudio2015`

     Pomocí přepínače `/layout` si můžete stáhnout téměř všechny instalační balíčky, nejen ty, které se vztahují na stahování stroje. Tento přístup poskytuje soubory, které potřebujete ke spuštění tohoto instalačního programu kdekoli a může být užitečné, pokud chcete nainstalovat součásti, které nebyly původně nainstalovány.

3. Po spuštění tohoto příkazu se zobrazí dialogové okno, které umožňuje změnit složku, ve které se má nacházet rozložení instalace offline.   Dále klikněte na tlačítko **Stáhnout.**

     Po úspěšném stažení balíčku by se měla zobrazit zpráva s textem **Setup Successful! Všechny zadané součásti byly úspěšně získány.**

4. Vyhledejte složku, kterou jste zadali dříve. (Například vyhledejte D:\VisualStudio2015.) Tato složka obsahuje vše, co potřebujete ke kopírování do sdíleného umístění nebo k instalaci média.

    > [!CAUTION]
    > V současné době sada Android SDK nepodporuje offline instalaci. Pokud nainstalujete položky instalace sady Android SDK do počítače, který není připojen k Internetu, instalace může selhat. Další informace naleznete v části Poradce při potížích s offline instalací v tomto tématu.

5. Spusťte instalaci z umístění souboru nebo z instalačního média.

## <a name="updating-an-offline-installation"></a>Aktualizace instalace offline
 Společnost Microsoft vydala několik aktualizací pro Visual Studio 2015. Chcete-li aktualizovat instalaci sady Visual Studio, jednoduše si stáhněte požadovanou edici ze stránky [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) stahování. Dále postupujte podle kroků popsaných v tomto tématu a vytvořte nové rozložení instalace offline a pak ho použijte k aktualizaci kopie Sady Visual Studio 2015.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a>Poradce při potížích s offline instalací
 Při instalaci offline z mezipaměti instalace offline se mohou zobrazit varovné zprávy o tom, že nelze nainstalovat některé součásti a balíčky. Následující tabulka obsahuje možná řešení pro tyto scénáře.

| Součást nebo balíček | Řešení |
|-|-|
| Dotfuscator a Analytics Community Edition 5.19.1 (pro edice Community, Professional a Enterprise sady Visual Studio, nainstalované v **systémech Windows 7 SP1** a **Windows Server 2008 R2**) | Pokud je v počítači offline spuštěn **systém Windows 7 SP1** nebo **Windows Server 2008 R2**, je třeba před instalací sady Visual Studio 2015 provést následující kroky:<br /><br /> 1. Nakonfigurujte soubor nebo webový server pro stahování souborů CTL.<br /><br /> 2. Přesměrujte adresu URL automatické aktualizace společnosti Microsoft do odpojeného prostředí.<br /><br /> Další informace naleznete na stránce [Konfigurace důvěryhodných kořenových adresářů a nepovolených certifikátů](https://technet.microsoft.com/library/dn265983.aspx) na webu Microsoft TechNet. |
| Nastavení sady Android SDK (úroveň rozhraní API) | Chcete-li nainstalovat balíčky sady Android SDK (úroveň rozhraní API), musíte mít připojení k internetu. Pokud jste v síti s omezeným přístupem, musíte při instalaci sady Visual Studio povolit přístup k následujícím adresám URL:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Další informace o řešení možných problémů s nastavením proxy serveru najdete v tématu [selhání instalace sady Visual Studio 2015 (nastavení sady Android SDK) za příspěvkem](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) blogu proxy. |
| Šablony položek rozšiřitelnosti sady Visual Studio<br /><br /> GitHub Extension for Visual Studio<br /><br /> Nástroje PowerShellu pro Visual Studio | Pokud nemáte připojení k internetu při instalaci Sady Visual Studio 2015, můžete použít speciální offline kanál pro generování rozložení instalace offline. **Poznámka:**  Tento speciální informační kanál obsahuje nejnovější aktualizace visual studia 2015. <br /><br /> Chcete-li vytvořit speciální offline kanál, spusťte následující příkaz: /layout *Drive:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml*<br /><br /> Například pro speciální offline kanál v anglickém jazyce sady Visual Studio 2015 Enterprise spusťte:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Úplný seznam adres URL, které můžete použít k vytvoření speciálního offline informačního kanálu v jazyce, který si vyberete, najdete v následující tabulce. |

 Pomocí následujících adres URL vytvořte speciální offline kanál specifický pro jazyk, jak je popsáno v tabulce výše.

|       Jazyk        |                            zprostředkovatele identity                            |
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