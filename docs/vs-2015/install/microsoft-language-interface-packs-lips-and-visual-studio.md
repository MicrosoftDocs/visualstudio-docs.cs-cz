---
title: Microsoft Language Interface sady LIP () | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 647935dce06d74b29271af130686a10fb8cfc1e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065035"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Sady LIP (Microsoft Language Interface Pack) a Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S použitím Windows Language Interface Pack (LIP), můžete nainstalovat jazykovou verzi Windows a pak nainstalovat různé uživatelského rozhraní jazykových sad. Uživatelské rozhraní jazykové sady poskytují lokalizovaná uživatelská rozhraní (UI) pro operační systém. Můžete například instalaci japonské jazykové sady rozhraní nad anglickou verzi systému Windows a pak přepnout jazyk uživatelského rozhraní Windows mezi anglické a japonština. Pomocí sady LIP může mít více jazykových verzí sady Windows na jednom počítači.

 Na počítačích, které mají sady LIP a více jazykových verzí sady Visual Studio nainstalovaný změna Windows nastavení jazyk zobrazení nastaví Windows a Visual Studio jsou nainstalovány odpovídající jazykové sady.

## <a name="limitations-of-multi-language-installations"></a>Omezení instalací Vícejazyčná verze
 Při instalaci odlišných jazykových verzí sady Visual Studio na stejném počítači, lze přepnout jen jazyky mezi odpovídající edice. Například pokud používáte anglickou verzi Express nainstalován, němčina Express Edition nainstalované a nainstalovaná edice Professional, jazyky lze přepnout jen pro edice Express, není pro edici Professional.

 Používá jednotný jazykové sady Visual Studio. K instalaci více než jedna jazyková verze sady těchto produktů, musíte nejprve nainstalovat produkt úplným jazykovým a potom nainstalovat jeden nebo více jazykových sad.

> [!NOTE]
>  Visual Studio nepodporuje instalaci více jazykových verzí produktu úplným jazykovým ve stejném počítači. Po instalaci jeden produkt s úplným jazykovým s použitím jazykové sady musíte přidat jazykové verze. Můžete nainstalovat více produktů úplným jazykovým edice Express ve stejném počítači.

### <a name="support-for-code-pages"></a>Podpora znakové stránky
 Některé nástroje Visual Studio nezobrazují text správně, když text obsahuje znaky, které nejsou v aktuální znakové stránce. Místo toho zobrazí otazníky nebo text je poškozený. Jsou ovlivněny následující nástroje nebo oblastech:

-   Servery nasazené s použitím FTP.

-   Názvy počítačů ne-ASCII v některé ovládací prvky.

-   Nástroje příkazového řádku, která spustí mimo sadu Visual Studio.

-   Průvodce migrací jazyka Visual Basic.

-   Kontejner testů ovládacích prvků ActiveX.

-   Prohlížeč objektů OLE/COM.

-   Nástroj pro ladění webové rozhraní ISAPI.

-   Projekty aplikace knihovny MFC, které mají obsah nápovědy HTML.

-   Aplikace Visual SourceSafe / uživatelského rozhraní SCCI spadne zpět na angličtinu po kompatibilní znakovou stránku.

-   Aplikace Visual SourceSafe nepodporuje názvy souborů Unicode.

-   Koncový uživatel definované znaků (soukromé použití zóny) nelze použít jako tokeny/identifikátory.

-   Znaky latinky Extended-B nelze zobrazit v některé aplikaci Visual Studio oknům, když Windows znaková stránka nastavena na východoasijské jazyky.

-   Toky textu, které se skládají ze znaků několik skriptů jazyka se může zobrazit glyfu některé znaky.

-   Kopírování a vkládání složitým řetězců do běžných ovládacích prvků může způsobit znak tvarování ztratí. Místo toho použijte odpovídající klávesnice jazyka se vstupním textem.

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>Pro správné zobrazení znaky, které nejsou zahrnuté v aktuální znakové stránce

1.  Klikněte na tlačítko **Start**, klikněte na tlačítko **ovládací panely**a pak otevřete **místní a jazykové nastavení** (nebo **oblasti** v [!INCLUDE[win8](../includes/win8-md.md)]).

    > [!NOTE]
    >  Musíte být správcem počítače, postupujte podle těchto kroků.

2.  Klikněte na tlačítko **Upřesnit** kartu.

3.  V **vyberte jazyk odpovídající jazykovou verzi kódování Unicode programy, které chcete použít** seznamu, vyberte jazyk, které právě používáte.

4.  Klikněte na tlačítko **OK**.

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>Změna jazyk používaný pro Text uživatelského rozhraní v sadě Visual Studio
 Když nainstalujete více jazykových verzí sady [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve stejném počítači, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uživatelského rozhraní výchozí hodnota je **totéž jako Windows Microsoft**. Toto nastavení znamená, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se zobrazí text uživatelského rozhraní v jazyce, který je zadán jako jazyk operačního systému.

> [!NOTE]
>  Pokud aplikace Visual Studio je nastaveno pro použití **totéž jako Windows Microsoft**a není nainstalovaná odpovídající jazyková sada Visual Studio, Visual Studio bude používat jazyk první instalaci sady Visual Studio.

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>Chcete-li nastavit jazyk, ve kterém se používá pro text uživatelského rozhraní v sadě Visual Studio

1. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.

2. V **možnosti** dialogového okna rozbalte **prostředí** a potom klikněte na tlačítko **mezinárodní nastavení**.

3. V **jazyk** seznamu, zvolte jazyk, ve kterém by se měla zobrazit text uživatelského rozhraní ve vývojovém prostředí.

    Chcete-li mít text uživatelského rozhraní IDE shoda zobrazovaný jazyk operačního systému, nastavení, vyberte **totéž jako Windows Microsoft**.

   Příkazu devenv můžete také nastavit jazyk, který se používá pro uživatelské rozhraní. Další informace najdete v tématu [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md).

## <a name="see-also"></a>Viz také
 [Mezinárodní nastavení, Prostředí, dialogové okno Možnosti](../ide/reference/international-settings-environment-options-dialog-box.md)