---
title: Začínáme s Visual Studio Tools for Unity | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: 12
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 9ed6cb4127ba57c6b9b84a32996968dbf9fac4fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762713"
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Začínáme s nástroji Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V této části se dozvíte, jak nainstalovat Visual Studio Tools for Unity a nakonfigurovat svým projektem Unity pro práci s aplikací Visual Studio.  
  
> [!IMPORTANT]
>  Unity 5.2 přidá integrovanou podporu pro Visual Studio Tools pro Unity 2.1, což zjednodušuje nastavení projektu. Abyste mohli využívat tohoto objektu, budete potřebovat Unity verze 5.2.0 nebo vyšší na Windows a Visual Studio Tools for Unity verze 2.1 nebo vyšší.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li použít Visual Studio Tools for Unity, budete potřebovat:  
  
-   Verze **sady Visual Studio** , který podporuje rozšíření, jako je například Visual Studio Community, Professional, Premium nebo Enterprise. Zdarma si můžete stáhnout Visual Studio Community.  
  
     [Stáhněte si Visual Studio Community](http://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   **Unity** verze 4.0.0 nebo vyšší. **Unity** verze 5.2.0 nebo novější, abyste mohli využívat výhody integrované podpory pro Visual Studio Tools for Unity verze 2.1 nebo vyšší.  
  
     [Stáhněte si Unity](https://unity3d.com/get-unity/download)  
  
## <a name="install-visual-studio-tools-for-unity"></a>Nainstalovat Visual Studio Tools for Unity  
 Stáhněte a nainstalujte Visual Studio Tools for Unity z Galerie sady Visual Studio. Bude potřeba nainstalovat balíček pravý pro vaši verzi sady Visual Studio. Ujistěte se, že k instalaci Visual Studio Tools for Unity verze 2.1 nebo vyšší, abyste mohli využívat výhody integrované podpory VSTU v Unity 5.2 nebo vyšší.  
  
-   Pro Visual Studio 2015 Community, Visual Studio 2015 Professional nebo Visual Studio 2015 Enterprise:  
  
     [Stáhněte si Visual Studio 2015 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  
  
-   Pro Visual Studio 2013 Community, Visual Studio 2013 Professional nebo Visual Studio 2013 Premium:  
  
     [Stáhněte si Visual Studio 2013 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  
  
-   Pro Visual Studio 2012 Professional nebo Visual Studio 2012 Premium:  
  
     [Stáhněte si Visual Studio 2012 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  
  
-   Pro Visual Studio 2010 Professional nebo Visual Studia 2010 Premium:  
  
     [Stáhněte si Visual Studio 2010 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  
  
> [!NOTE]
>  Expresní verze sady Visual Studio nepodporují rozšíření, jako je Visual Studio Tools for Unity. Visual Studio Community je bezplatné verze sady Visual Studio, které podporuje Visual Studio Tools for Unity a další rozšíření. Pro většinu uživatelů Visual Studio Community je vhodnější než Express.  
  
## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>Svůj první projekt Unity s Visual Studio Tools for Unity  
 Teď, když máte všechno, co potřebujete, jste připraveni svůj první projekt Unity pomocí sady Visual Studio. Nastavení projektu Unity, se liší v závislosti na tom, jaké verze rozhraní Unity a Visual Studio Tools for Unity jsou nainstalované. Proveďte následující postup pro verzi Unity a Visual Studio Tools for Unity, kterou jste nainstalovali.  
  
### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>Unity 5.2 a vyšší (vyžaduje VSTU 2.1 nebo vyšší)  
 Od verze Unity 5.2, nepotřebujete k importu unitypackage nástroje sady Visual Studio do vašich projektů. Pokud váš projekt importuje tento unitypackage, Unity 5.2 ignoruje ji a přímo z nainstalovaného umístění načte Visual Studio Tools for Unity.  
  
#### <a name="1---create-a-unity-project"></a>1 – Vytvoření projektu Unity  
 Pokud již máte zkušenosti s Unity, můžete vytvořit nový projekt nebo načíst svůj vlastní. Pokud načítáte projekt, který se importovat unitypackage nástroje sady Visual Studio používat Visual Studio Tools for Unity pomocí předchozí verze služby Unity, doporučujeme odebrat odstraněním UnityVS adresáře.  
  
 Jinak pokud začínáte Unity, začněte v malém se základním kurzem. Na stránce Unity další kurzy na ukázkové projekty, které můžete začít s a poznatků, na které můžete naučit ze sestavení vašich vlastních her pomocí Unity. Stránka Unity další má snadno následující kurzy pro několik různých hry.  
  
 [Kurzy – stránka Další Unity](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 – konfigurace Unity Editor používat Visual Studio Tools for Unity  
 Pokud chcete povolit projektu použít Visual Studio Tools for Unity, stačí nastavte Visual Studio jako editor externích skriptů. V Unity editoru v hlavní nabídce zvolte **Předvolby úprav**; potom v **Unity Předvolby** dialogovém okně zvolte **externích nástrojů**. Dále nastavte **externí Editor skriptů** vlastnost na verzi sady Visual Studio, kterou chcete použít (Visual Studio Tools for Unity musí být nainstalována tato verze sady Visual Studio) a ujistěte se, že **Editor připojení** je nastavena.  
  
 Ujistěte se, že tento integrovanou podporu pro Visual Studio Tools pro Unity je nyní povolená, najdete v článku **o Unity** dialogového okna. V editoru Unity v hlavní nabídce zvolte **nápovědy o Unity.** Pokud Visual Studio Tools for Unity je nainstalován a správně nakonfigurovaná, zobrazí se vám zpráva v levém dolním rohu **o Unity** dialogového okna.  
  
 A konečně, ujistěte se, že nastavíte cíl sestavení prostřednictvím **nastavení sestavení** stránky a že **ladění skriptů** je povolená.  
  
 ![Konfigurace nastavení buildu Unity pro ladění. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3 – Spusťte sadu Visual Studio z Unity editoru  
 Od verze Unity 5.2 **Visual Studio Tools** nabídka rozšíření už nepotřebujete spusťte sadu Visual Studio nebo konfigurovat Visual Studio Tools for Unity. Místo toho jednou Visual Studio je nakonfigurovaný jako editor externích skriptů, prostě vybrat soubor skriptu z Unity editoru a váš kód se otevřou v sadě Visual Studio.  
  
### <a name="previous-versions-of-unity-pre-52"></a>Předchozí verze Unity (pre-5.2)  
 Před 5.2 Unity nebyl žádný integrovanou podporu pro Visual Studio Tools for Unity. Místo toho každého projektu došlo k importu unitypackage nástroje sady Visual Studio a nakonfigurujte další nastavení projektu, chcete-li použít Visual Studio Tools for Unity.  
  
#### <a name="1---create-a-unity-project"></a>1 – Vytvoření projektu Unity  
 Pokud již máte zkušenosti s Unity, můžete vytvořit nový projekt nebo načíst svůj vlastní. Pokud začínáte nový projekt, importujte unitypackage nástroje sady Visual Studio při jeho vytvoření.  
  
 Jinak pokud začínáte Unity, začněte v malém se základním kurzem. Na stránce Unity další kurzy na ukázkové projekty, které můžete začít s a poznatků, na které můžete naučit ze sestavení vašich vlastních her pomocí Unity. Stránka Unity další má snadno následující kurzy pro několik různých hry.  
  
 [Kurzy – stránka Další Unity](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 – konfigurace Unity Editor používat Visual Studio Tools for Unity  
 Pokud začínáte z existujícího projektu Unity nebo nenaimportovali unitypackage nástroje sady Visual Studio při vytváření projektu, musíte importovat unitypackage nyní. V editoru Unity v hlavní nabídce zvolte **prostředky, importovat balíček, Visual Studio 2015 Tools** (zobrazí se možnost pro verzi sady Visual Studio, které jste si nainstalovali).  
  
 ![Importujte balíček VSTU ve vašem Unity projektu. ](../cross-platform/media/vstu-configure-unity-import-vstu.png "vstu_configure_unity_import_vstu")  
  
 A konečně, ujistěte se, že nastavíte cíl sestavení prostřednictvím **nastavení sestavení** stránky a že **ladění skriptů** je povolená.  
  
 ![Konfigurace nastavení buildu Unity pro ladění. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-unity-editor"></a>3 – Spusťte sadu Visual Studio z Unity editoru  
 Posledním krokem je spuštění sady Visual Studio z Unity. To vytvoří řešení sady Visual Studio pro váš projekt a pak ho otevře v sadě Visual Studio.  
  
 V Unity editoru v hlavní nabídce zvolte **nástroje sady Visual Studio, otevřete v sadě Visual Studio**.  
  
 ![Otevřete svůj projekt unity v sadě Visual Studio. ](../cross-platform/media/vstu-configure-open-in-visual-studio.png "vstu_configure_open_in_visual_studio")  
  
## <a name="next-steps"></a>Další kroky  
 Informace o práci s a ladit svým projektem Unity v sadě Visual Studio najdete v tématu [pomocí Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).  
  
## <a name="see-also"></a>Viz také  
 [Domovská stránka Unity](http://unity3d.com)

