---
title: Začínáme s Visual Studio Tools for Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: 12
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: f110b8d6f7ab05d5a1b6942cd9ec599a8d8619b7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299832"
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Začínáme s nástroji Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této části se dozvíte, jak nainstalovat Visual Studio Tools for Unity a nakonfigurovat svůj projekt Unity pro práci se sadou Visual Studio.  
  
> [!IMPORTANT]
> Unity 5,2 přidává integrovanou podporu pro Visual Studio Tools for Unity 2,1, která zjednodušuje nastavení projektu. Abyste to mohli využít, budete potřebovat Unity verze 5.2.0 nebo vyšší ve Windows a Visual Studio Tools for Unity verze 2,1 nebo vyšší.  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete použít Visual Studio Tools for Unity, budete potřebovat:  
  
- Verze sady **Visual Studio** , která podporuje rozšíření, jako je Visual Studio Community, Professional, Premium nebo Enterprise. Visual Studio Community si můžete zdarma stáhnout.  
  
     [Stáhněte si Visual Studio Community](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
- Verze **Unity** 4.0.0 nebo vyšší; **Unity** verze 5.2.0 nebo vyšší, abyste mohli využít integrovanou podporu pro Visual Studio Tools for Unity verze 2,1 nebo vyšší.  
  
     [Stáhnout Unity](https://unity3d.com/get-unity/download)  
  
## <a name="install-visual-studio-tools-for-unity"></a>Nainstalovat Visual Studio Tools for Unity  
 Stáhněte a nainstalujte Visual Studio Tools for Unity z galerie sady Visual Studio. Budete muset nainstalovat správný balíček pro vaši verzi sady Visual Studio. Nezapomeňte nainstalovat Visual Studio Tools for Unity verze 2,1 nebo vyšší, abyste mohli využít integrovanou podporu VSTU v Unity 5,2 nebo vyšších verzích.  
  
- Pro Visual Studio 2015 Community, Visual Studio 2015 Professional nebo Visual Studio 2015 Enterprise:  
  
     [Stáhnout Visual Studio 2015 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  
  
- Pro Visual Studio 2013 komunita Visual Studio 2013 Professional nebo Visual Studio 2013 Premium:  
  
     [Stažení Visual Studio 2013 nástrojů pro Unity](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  
  
- Pro Visual Studio 2012 Professional nebo Visual Studio 2012 Premium:  
  
     [Stáhnout Visual Studio 2012 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  
  
- Pro Visual Studio 2010 Professional nebo Visual Studio 2010 Premium:  
  
     [Stáhnout Visual Studio 2010 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  
  
> [!NOTE]
> Verze Express sady Visual Studio nepodporují rozšíření, jako je Visual Studio Tools for Unity. Visual Studio Community je bezplatná verze sady Visual Studio, která podporuje Visual Studio Tools for Unity a další rozšíření. Pro většinu uživatelů je Visual Studio Community lepší volbou než expresní.  
  
## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>Váš první projekt Unity s Visual Studio Tools for Unity  
 Teď, když máte všechno, co potřebujete, jste připraveni na svůj první projekt Unity se sadou Visual Studio. Nastavení projektu Unity se liší v závislosti na tom, jaké verze Unity a Visual Studio Tools for Unity jsou nainstalované. Použijte následující postup pro verzi Unity a Visual Studio Tools for Unity, kterou jste nainstalovali.  
  
### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>Unity 5,2 a vyšší (vyžaduje VSTU 2,1 nebo novější)  
 Od Unity 5,2 už nemusíte naimportovat Visual Studio Tools unitypackage do vašich projektů. Pokud projekt importuje toto unitypackage, Unity 5,2 ho ignoruje a přímo načte Visual Studio Tools for Unity z jeho nainstalovaného umístění.  
  
#### <a name="1---create-a-unity-project"></a>1\. vytvoření projektu Unity  
 Pokud již máte zkušenosti s Unity, můžete vytvořit nový projekt nebo si sami načíst vlastní. Pokud načítáte projekt, který importoval Visual Studio Tools unitypackage pro použití Visual Studio Tools for Unity s předchozí verzí Unity, doporučujeme, abyste ho odebrali odstraněním adresáře UnityVS.  
  
 Jinak, pokud s Unity začínáte, začněte s základním kurzem. Navštivte stránku s výukou Unity, kde najdete kurzy k příkladům projektů, které můžete začít používat, a lekce, ze kterých se můžete dozvědět, abyste si mohli vytvořit vlastní hru s Unity. Stránka s výukou Unity obsahuje snadno ovladatelné kurzy pro několik různých her.  
  
 [Kurzy – Stránka s učením Unity](https://learn.unity.com/tutorials)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 – konfigurace editoru Unity pro použití Visual Studio Tools for Unity  
 Chcete-li povolit, aby váš projekt používal Visual Studio Tools for Unity, stačí nastavit sadu Visual Studio jako svůj externí editor skriptu. V editoru Unity v hlavní nabídce vyberte možnost **Upravit, předvolby**; pak v dialogovém okně **Předvolby Unity** zvolte **externí nástroje**. Dále nastavte vlastnost **editoru externích skriptů** na verzi sady Visual Studio, kterou chcete použít (Visual Studio Tools for Unity musí být nainstalována pro tuto verzi sady Visual Studio) a ujistěte se, že je nastavena vlastnost **připojení editoru** .  
  
 Pokud chcete mít jistotu, že je teď povolená integrovaná podpora pro Visual Studio Tools for Unity, přečtěte si dialogové okno **o Unity** . V editoru Unity v hlavní nabídce klikněte na tlačítko **help (informace o Unity).** Pokud je nainstalovaná a správně nakonfigurovaná Visual Studio Tools for Unity, zobrazí se v levém dolním rohu dialogového okna **o Unity** zpráva.  
  
 Nakonec se ujistěte, že jste nastavili cíl sestavení pomocí stránky **nastavení sestavení** a že je povolené **ladění skriptu** .  
  
 ![Nakonfigurujte nastavení sestavení Unity pro ladění.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3\. spuštění sady Visual Studio z editoru Unity  
 Od Unity 5,2 již není nabídka rozšíření **Visual Studio Tools** potřebná ke spuštění sady Visual Studio nebo ke konfiguraci Visual Studio Tools for Unity. Místo toho, když je Visual Studio nakonfigurované jako externí editor skriptu, stačí zvolit soubor skriptu z editoru Unity a váš kód se otevře v aplikaci Visual Studio.  
  
### <a name="previous-versions-of-unity-pre-52"></a>Předchozí verze Unity (pre-5,2)  
 Před Unity 5,2 neexistovala žádná integrovaná podpora pro Visual Studio Tools for Unity. Místo toho musel každý projekt importovat Visual Studio Tools unitypackage a nakonfigurovat další nastavení projektu, aby bylo možné použít Visual Studio Tools for Unity.  
  
#### <a name="1---create-a-unity-project"></a>1\. vytvoření projektu Unity  
 Pokud již máte zkušenosti s Unity, můžete vytvořit nový projekt nebo si sami načíst vlastní. Pokud spouštíte nový projekt, importujte Visual Studio Tools unitypackage při jeho vytváření.  
  
 Jinak, pokud s Unity začínáte, začněte s základním kurzem. Navštivte stránku s výukou Unity, kde najdete kurzy k příkladům projektů, které můžete začít používat, a lekce, ze kterých se můžete dozvědět, abyste si mohli vytvořit vlastní hru s Unity. Stránka s výukou Unity obsahuje snadno ovladatelné kurzy pro několik různých her.  
  
 [Kurzy – Stránka s učením Unity](https://learn.unity.com/tutorials)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 – konfigurace editoru Unity pro použití Visual Studio Tools for Unity  
 Pokud začínáte z existujícího projektu Unity nebo jste neimportovali Visual Studio Tools unitypackage při vytváření projektu, budete muset unitypackage hned importovat. V editoru Unity v hlavní nabídce vyberte **prostředky, importovat balíček, Visual Studio 2015 Tools** (měli byste vidět možnost pro verzi sady Visual Studio, kterou jste nainstalovali).  
  
 ![Importujte balíček VSTU do projektu Unity.](../cross-platform/media/vstu-configure-unity-import-vstu.png "vstu_configure_unity_import_vstu")  
  
 Nakonec se ujistěte, že jste nastavili cíl sestavení pomocí stránky **nastavení sestavení** a že je povolené **ladění skriptu** .  
  
 ![Nakonfigurujte nastavení sestavení Unity pro ladění.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-unity-editor"></a>3\. spuštění sady Visual Studio z editoru Unity  
 Posledním krokem je spuštění sady Visual Studio z Unity. Tím se vytvoří řešení sady Visual Studio pro váš projekt a potom se otevře v aplikaci Visual Studio.  
  
 V editoru Unity v hlavní nabídce vyberte **Visual Studio Tools, otevřete v aplikaci Visual Studio**.  
  
 ![Otevřete svůj projekt Unity v aplikaci Visual Studio.](../cross-platform/media/vstu-configure-open-in-visual-studio.png "vstu_configure_open_in_visual_studio")  
  
## <a name="next-steps"></a>Další kroky  
 Informace o tom, jak pracovat s projektem Unity a ladit ho v aplikaci Visual Studio, najdete v tématu [použití Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).  
  
## <a name="see-also"></a>Viz také  
 [Domovská stránka Unity](https://unity.com/)
