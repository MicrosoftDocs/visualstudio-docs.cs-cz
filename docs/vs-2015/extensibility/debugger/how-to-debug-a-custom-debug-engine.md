---
title: 'Postupy: ladění vlastního ladicího stroje | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7e710cec4536a5a1327580e56c60cb23ca36f4c
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "64797393"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Postupy: Ladění vlastního ladicího stroje
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typ projektu spustí ladicí modul (DE) z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody. To znamená, že DE se spustí pod kontrolou instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] řízení typu projektu. Nicméně, tato instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nemůže LADIT de. Níže jsou uvedené kroky, které vám umožní ladit vlastní DE.  
  
> [!NOTE]
> : V postupu "ladění vlastního ladicího modulu" je nutné počkat na spuštění příkazu DE, aby bylo možné se k němu připojit. Pokud umístíte okno se zprávou poblíž začátku ovládacího panelu DE, který se zobrazí při zahájení spuštění, můžete se v tomto okamžiku připojit a pak zrušit zaškrtnutí okna se zprávou, abyste mohli pokračovat. Tímto způsobem můžete zachytit všechny události DE.  
  
> [!WARNING]
> Předtím, než se pokusíte provést následující postupy, musíte mít nainstalováno vzdálené ladění. Podrobnosti najdete v tématu [vzdálené ladění](../../debugger/remote-debugging.md) .  
  
### <a name="debugging-a-custom-debug-engine"></a>Ladění vlastního ladicího stroje  
  
1. Spusťte msvsmon.exe, sledování vzdáleného ladění.  
  
2. V nabídce **nástroje** v msvsmon.exe vyberte **Možnosti** a otevřete tak dialogové okno **Možnosti** .  
  
3. Vyberte možnost bez ověřování a klikněte na tlačítko **OK**.  
  
4. Spusťte instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a otevřete vlastní de Project.  
  
5. Spusťte druhou instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a otevřete svůj vlastní projekt, který SPUSTÍ de (pro vývoj), obvykle se jedná o experimentální podregistr registru, který je nastaven při instalaci VSIP).  
  
6. V této druhé instanci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] načtěte zdrojový soubor z vlastního projektu a spusťte program, který se má ladit. Chvíli počkejte, aby bylo možné načíst DE Load, nebo počkejte, až se zarážka dorazí.  
  
7. V první instanci nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (s projektem de) vyberte možnost **připojit k procesu** z nabídky **ladění** .  
  
8. V dialogovém okně **připojit k procesu** změňte **přenos** na **vzdálené (nativní pouze bez ověřování)**.  
  
9. Změňte **kvalifikátor** na název počítače (Poznámka: existuje historie položek, takže je třeba zadat tento název pouze jednou).  
  
10. V seznamu **procesy k dispozici** vyberte instanci nástroje de, která běží, a klikněte na tlačítko **připojit** .  
  
11. Poté, co byly symboly načteny do DE, umístěte zarážky do kódu DE.  
  
12. Pokaždé, když zastavíte a pak znovu spustíte proces ladění, opakujte kroky 6 až 10.  
  
### <a name="debugging-a-custom-project-type"></a>Ladění vlastního typu projektu  
  
1. Spusťte [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v normálním podregistru a načtěte projekt typu projektu (Toto je zdroj pro typ projektu, nikoli instanci typu projektu).  
  
2. Otevřete vlastnosti projektu a přejdete na stránku **ladění** . Pro **příkaz**zadejte cestu k [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (ve výchozím nastavení to je *[jednotka]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3. Pro **argumenty příkazu**zadejte `/rootsuffix exp` experimentální podregistr registru (vytvořený při instalaci VSIP).  
  
4. Potvrďte změny kliknutím na tlačítko **OK** .  
  
5. Stisknutím klávesy F5 spusťte typ projektu. Tím se spustí druhá instance [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
6. V tomto okamžiku můžete umístit zarážky do zdrojového kódu typu projektu.  
  
7. Ve druhé instanci aplikace [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] načtěte nebo vytvořte novou instanci typu projektu. Během zátěže nebo vytvoření může docházet ke zarážce.  
  
8. Ladit typ projektu.  
  
9. Pokud se rozhodnete ladit proces spuštění příkazu DE, můžete postupovat podle postupu v tématu "ladění vlastního ladicího stroje", aby se připojil ke složce DE po jejím spuštění. Tím získáte tři instance, které jsou [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spuštěny: jeden pro svůj zdroj typu projektu, druhý pro instanci typu projektu a třetí připojený k de.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)
