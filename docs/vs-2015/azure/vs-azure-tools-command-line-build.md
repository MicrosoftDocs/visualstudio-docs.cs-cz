---
title: Sestavení z příkazového řádku Azure | Dokumentace Microsoftu
description: Sestavení z příkazového řádku Azure
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: fce752d91ebaa765e18efef117a3b6efe750119c
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003342"
---
# <a name="building-azure-projects-from-the-command-line"></a>Sestavování projektů Azure z příkazového řádku
Microsoft Build Engine (MSBuild) můžete vytvářet produkty v prostředích sestavení testovacího prostředí, kde není nainstalovaná sada Visual Studio. Nástroj MSBuild používá formát XML pro soubory projektu, které je rozšiřitelný a plně podporovaný microsoftem. Pomocí nástroje MSBuild formát souboru, můžete popsat, co položky musí být vytvořená pro jeden nebo více platformách a konfiguracích.

Můžete také spustit nástroj MSBuild na příkazovém řádku a v tomto tématu popisuje tento přístup. Nastavením vlastnosti na příkazovém řádku můžete vytvářet konkrétní konfigurace projektu. Podobně můžete také definovat cíle, které sestavení nástroje MSBuild. Další informace o parametrech příkazového řádku a nástroje MSBuild naleznete v tématu [MSBuild Reference k příkazovému řádku](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Parametry nástroje MSBuild
Chcete-li spustit nástroj MSBuild s je nejjednodušší způsob, jak vytvořit balíček `/t:Publish` možnost. Ve výchozím nastavení, tento příkaz vytvoří adresář ve vztahu ke kořenové složce projektu, jako například `<ProjectDirectory>\bin\Configuration\app.publish\`. Když vytvoříte projekt Azure, jsou generovány dva soubory: balíček samotný soubor a související konfigurační soubor:

* Soubor balíčku (`project.cspkg`)
* Konfigurační soubor (`ServiceConfiguration.TargetProfile.cscfg`)

Ve výchozím nastavení obsahuje každý projekt Azure jeden soubor konfigurace služby pro místní sestavení (ladění) a druhý pro sestavení můžou v cloudu (přípravné nebo produkční). Můžete však přidat nebo odebrat soubory konfigurace služby podle potřeby. Při vytváření balíčku v rámci sady Visual Studio, zobrazí se výzva který soubor konfigurace služby zahrnout spolu s balíček. Při vytváření balíčku pomocí nástroje MSBuild je standardní součástí místní služby konfigurační soubor. Chcete-li zahrnout jiný soubor konfigurace služby, nastavte `TargetProfile` vlastnost příkaz MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Pokud chcete použít jiný adresář pro uložené balíček a konfigurační soubory, nastavte cestu s použitím `/p:PublishDir=Directory\` možností, včetně koncové oddělovače zpětné lomítko.

## <a name="next-steps"></a>Další kroky
Jakmile je balíček vytvořen, můžete ji nasadit do Azure.