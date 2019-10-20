---
title: Principy konfigurací sestavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a7e7c184fd150c46b3a8be0ec583d4223487ad32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672760"
---
# <a name="understanding-build-configurations"></a>Principy konfigurací sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete uložit různé konfigurace vlastností řešení a projektu pro použití v různých typech sestavení. Chcete-li vytvořit, vybrat, upravit nebo odstranit konfiguraci, můžete použít **Configuration Manager**. Chcete-li jej otevřít, v panelu nabídek vyberte v poli **Snadné spuštění** možnost **sestavit**, **Configuration Manager**nebo pouze **Konfigurace** typu. Můžete také použít seznam **Konfigurace řešení** na panelu nástrojů **standardní** k výběru konfigurace nebo otevření **Configuration Manager**.

> [!NOTE]
> Pokud nemůžete najít nastavení konfigurace řešení na panelu nástrojů a nemůžete získat přístup k **Configuration Manager**, může být použito nastavení pro vývoj [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Další informace najdete v tématu [Postupy: Správa konfigurací pomocí Visual Basic nastavení pro vývojáře](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

 Ve výchozím nastavení jsou konfigurace ladění a vydání zahrnuty v projektech, které jsou vytvořeny pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] šablon. Konfigurace ladění podporuje ladění aplikace a konfigurace vydaných verzí vytvoří verzi aplikace, kterou lze nasadit. Další informace najdete v tématu [Postupy: nastavení ladění a konfigurací vydání](../debugger/how-to-set-debug-and-release-configurations.md). Můžete také vytvořit vlastní konfigurace řešení a konfigurace projektu. Další informace najdete v tématu [Postup: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Konfigurace řešení
 Konfigurace řešení určuje, jak mají být projekty v řešení sestaveny a nasazeny. Chcete-li upravit konfiguraci řešení nebo definovat nový, v **Configuration Manager**v části **Konfigurace aktivního řešení**vyberte možnost **Upravit** nebo **Nový**.

 Každá položka v poli **kontexty projektu** v konfiguraci řešení představuje projekt v řešení. Pro každou kombinaci **aktivní konfigurace řešení** a **platformy aktivního řešení**můžete nastavit, jak se má každý projekt používat. (Další informace o platformách řešení najdete v tématu [porozumění platformám sestavení](../ide/understanding-build-platforms.md).)

> [!NOTE]
> Při definování nové konfigurace řešení a zaškrtnutí políčka **vytvořit nové konfigurace projektu** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky přiřadí novou konfiguraci všem projektům. Podobně, při definování nové platformy řešení a zaškrtnutí políčka **vytvořit nové projektové platformy** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky přiřadí novou platformu všem projektům. Také Pokud přidáte projekt, který cílí na novou platformu, Visual Studio přidá tuto platformu do seznamu platforem řešení a přiřadí je ke všem projektům.
>
> Můžete přesto upravit nastavení pro každý projekt.

 Aktivní konfigurace řešení také poskytuje kontext rozhraní IDE. Například pokud pracujete na projektu a konfigurace určuje, že bude sestavena pro mobilní zařízení, zobrazí **Sada nástrojů** pouze položky, které lze použít v projektu mobilního zařízení.

## <a name="project-configurations"></a>Konfigurace projektu
 Konfigurace a platforma, které cílí na projekt, se používají společně k určení vlastností, které mají být použity při sestavení. Projekt může mít jinou sadu definic vlastností pro každou kombinaci konfigurace a platformy. Chcete-li upravit vlastnosti projektu, můžete použít jeho stránky vlastností. (V **Průzkumník řešení**otevřete místní nabídku pro projekt a pak zvolte možnost **vlastnosti**.)

 Pro každou konfiguraci projektu můžete podle potřeby definovat vlastnosti závislé na konfiguraci. Například pro konkrétní sestavení můžete nastavit, které položky projektu budou zahrnuty a které výstupní soubory budou vytvořeny, kde budou vloženy a jak budou optimalizovány.

 Konfigurace projektu se můžou výrazně lišit. Například vlastnosti jedné konfigurace můžou určit, že se má jeho výstupní soubor optimalizovat tak, aby vybíral minimální místo, zatímco jiná konfigurace může určit, že jeho spustitelný soubor běží s maximální rychlostí.

 Konfigurace projektu jsou uloženy podle řešení, nikoli podle uživatele, aby mohly být sdíleny týmem.

 Přestože závislosti projektu jsou nezávislé na konfiguraci, budou sestaveny pouze projekty, které jsou zadány v aktivní konfiguraci řešení.

## <a name="how-visual-studio-assigns-project-configurations"></a>Jak Visual Studio přiřadí konfigurace projektu
 Pokud definujete novou konfiguraci řešení a nekopírujete nastavení z existujícího projektu, Visual Studio použije následující kritéria k přiřazení výchozích konfigurací projektu. Kritéria jsou vyhodnocována v uvedeném pořadí.

1. Pokud má projekt název konfigurace ( *\<configuration název > \<platform název >* ), který přesně odpovídá názvu nové konfigurace řešení, je tato konfigurace přiřazena. V názvech konfigurace se nerozlišují velká a malá písmena.

2. Pokud má projekt název konfigurace, ve kterém část konfigurace-název odpovídá nové konfiguraci řešení, je tato konfigurace přiřazena, ať už část platformy odpovídá nebo ne.

3. Pokud se stále neshoduje, první konfigurace, která je uvedená v projektu, je přiřazena.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Jak Visual Studio přiřadí konfigurace řešení
 Když vytvoříte konfiguraci projektu (v **Configuration Manager**kliknutím na možnost **Nový** v rozevírací nabídce ve sloupci **Konfigurace** pro daný projekt) a zaškrtnutím políčka **vytvořit nové konfigurace řešení** , vizuál Studio vyhledá konfiguraci řešení se stejným názvem a sestaví projekt na všech podporovaných platformách. V některých případech aplikace Visual Studio přejmenuje existující konfigurace řešení nebo definuje nové.

 Visual Studio používá následující kritéria k přiřazení konfigurací řešení.

- Pokud konfigurace projektu nespecifikuje platformu nebo určuje jenom jednu platformu, pak se v konfiguraci řešení, jejíž název shoduje s názvem nové konfigurace projektu, najde nebo přidá. Výchozí název této konfigurace řešení nezahrnuje název platformy; má podobu *\<project název konfigurace >* .

- Pokud projekt podporuje více platforem, je konfigurace řešení buď nalezena, nebo přidána pro každou podporovanou platformu. Název každé konfigurace řešení zahrnuje název konfigurace projektu i název platformy a má formu *\<project název konfigurace > \<platform název >* .

## <a name="see-also"></a>Viz také
 [Návod: Vytvoření aplikace](../ide/walkthrough-building-an-application.md) [kompilování a sestavování](../ide/compiling-and-building-in-visual-studio.md) [řešení a projektů](../ide/solutions-and-projects-in-visual-studio.md) [C/C++ sestavit odkazy](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [příkazového řádku devenv](../ide/reference/devenv-command-line-switches.md)
