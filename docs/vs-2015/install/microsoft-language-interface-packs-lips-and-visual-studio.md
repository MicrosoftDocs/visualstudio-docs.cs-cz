---
title: Jazykové sady Microsoft Language Interface Pack (LIP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- text [Visual Studio], multiple languages
- Multilingual User Interface [Visual Studio]
- language switching [Visual Studio]
- MUI [Visual Studio]
- multiple language support [Visual Studio SDK]
- Windows Multilingual User Interface
- UI text language [Visual Studio]
- languages, multiple language support
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 503f97d1530f8d22184f42a2452046782a997c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814327"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Sady LIP (Microsoft Language Interface Pack) a Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí sady Language Interface Pack (LIP) systému Windows můžete nainstalovat jazykovou verzi systému Windows a poté nainstalovat různé jazykové sady uživatelského rozhraní. Jazykové sady uživatelského rozhraní poskytují lokalizované uživatelské rozhraní (UI) pro operační systém. Například můžete nainstalovat sadu japonských jazykových rozhraní do anglické verze systému Windows a potom přepnout jazyk uživatelského rozhraní systému Windows mezi japonštinou a anglickou verzí. Pomocí sad LIP můžete mít v jednom počítači více jazykových verzí systému Windows.

 V počítačích, ve kterých jsou nainstalovány sady LIP a více jazykových verzí sady Visual Studio, změna nastavení jazyka zobrazení systému Windows nastaví systém Windows i sadu Visual Studio, pokud jsou nainstalovány odpovídající jazykové sady.

## <a name="limitations-of-multi-language-installations"></a>Omezení instalací s více jazyky
 Když instalujete různé jazykové verze sady Visual Studio do stejného počítače, můžete přepínat jazyky jenom mezi vyhovujícími edicemi. Například pokud máte nainstalovanou anglickou verzi English Express, nainstalovanou Německo Express Edition a nainstalovanou edici Professional, můžete přepínat jenom jazyky pro edice Express, ne pro edici Professional.

 Sada Visual Studio používá sjednocenou jazykovou sadu. Chcete-li nainstalovat více než jednu jazykovou verzi těchto produktů, je třeba nejprve nainstalovat úplný jazykový produkt a pak nainstalovat jednu nebo více jazykových sad.

> [!NOTE]
> Visual Studio nepodporuje instalaci více jazykových verzí plného jazykového produktu do stejného počítače. Po instalaci jednoho kompletního jazykového produktu je nutné přidat jazykové verze pomocí jazykových sad. Na stejný počítač můžete i nadále instalovat více úplných jazykových produktů edice Express.

### <a name="support-for-code-pages"></a>Podpora pro znakové stránky
 Některé nástroje sady Visual Studio nezobrazuje text správně, pokud text obsahuje znaky, které nejsou na aktuální znakové stránce. Místo toho se zobrazí otazníky nebo je text poškozený. Ovlivněny jsou následující nástroje nebo oblasti:

- Weby nasazené pomocí FTP

- Názvy počítačů bez ASCII v některých ovládacích prvcích.

- Nástroje příkazového řádku, které se spouštějí mimo sadu Visual Studio.

- Průvodce migrací Visual Basic.

- Kontejner testu ovládacího prvku ActiveX

- Prohlížeč objektů OLE/COM.

- Nástroj pro ladění webu ISAPI.

- Projekty aplikace MFC, které obsahují obsah HTML Help.

- Uživatelské rozhraní Visual SourceSafe/SCCI se vrátí do angličtiny, pokud je k dispozici nekompatibilní znaková stránka.

- Visual SourceSafe nepodporuje názvy souborů Unicode.

- Znaky definované koncovým uživatelem (zóna privátního použití) nelze použít jako tokeny nebo identifikátory.

- V některých oknech nástrojů sady Visual Studio se znaky rozšířené verze latinky a B nedají zobrazit, pokud je znaková stránka Windows nastavená na východoasijský jazyk.

- Text, který se skládá ze znaků z více jazykových skriptů, může u některých znaků zobrazit výchozí glyf.

- Kopírování a vkládání složitých řetězců skriptu do běžných ovládacích prvků může způsobit ztrátu tvaru znaků. Místo toho použijte k zadání textu odpovídající jazykovou klávesnici.

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>Pro správné zobrazení znaků, které nejsou součástí aktuální znakové stránky

1. Klikněte na tlačítko **Start**, klikněte na položku **Ovládací panely**a pak otevřete **panel místní a jazykové nastavení** (nebo **oblast v oblasti** [!INCLUDE[win8](../includes/win8-md.md)] ).

    > [!NOTE]
    > Chcete-li provést tento postup, musíte být správcem počítače.

2. Klikněte na kartu **Upřesnit** .

3. V seznamu **Vyberte jazyk, který se bude shodovat s jazykovou verzí programů, které chcete použít** , vyberte jazyk, který aktuálně používáte.

4. Klikněte na **OK**.

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Změna jazyka používaného pro text uživatelského rozhraní v aplikaci Visual Studio
 Když nainstalujete více jazykových verzí nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na stejný počítač, použije se [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] výchozí uživatelské rozhraní **stejné jako v systému Microsoft Windows**. Toto nastavení označuje, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se zobrazí text uživatelského rozhraní v jazyce, který je určen jako jazyk zobrazení pro operační systém.

> [!NOTE]
> Pokud je sada Visual Studio nastavena na použití **stejné jako v systému Microsoft Windows**a není nainstalována shodná jazyková sada sady Visual Studio, sada Visual Studio použije jazyk první instalace sady Visual Studio.

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>Nastavení jazyka, který se používá pro text uživatelského rozhraní v sadě Visual Studio

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. V dialogovém okně **Možnosti** rozbalte položku **prostředí** a klikněte na možnost **mezinárodní nastavení**.

3. V seznamu **jazyk** vyberte jazyk, ve kterém se má text uživatelského rozhraní zobrazit ve vývojovém prostředí.

    Chcete-li, aby text uživatelského rozhraní v integrovaném vývojovém prostředí odpovídal nastavení jazyka zobrazení operačního systému, vyberte **stejné jako v systému Microsoft Windows**.

   Pomocí příkazu devenv můžete také nastavit jazyk, který se používá pro uživatelské rozhraní. Další informace najdete v tématu [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).

## <a name="see-also"></a>Viz také
 [Mezinárodní nastavení, Prostředí, dialogové okno Možnosti](../ide/reference/international-settings-environment-options-dialog-box.md)