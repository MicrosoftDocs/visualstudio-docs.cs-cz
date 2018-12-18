---
title: 'Postupy: Ladění vlastního ladicího stroje | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdc01eec9982f7e3a03cd84424bc56b031846a7d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858859"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Postupy: Ladění vlastního ladicího stroje
Typ projektu spustí ladicí stroj (DE) z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody. To znamená, že je DE spuštění pod kontrolou instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] řízení typ projektu. Ale tuto instanci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nelze ladit DE. Následují kroky, které umožňují ladění vlastního DE.  
  
> [!NOTE]
>  : V postupu "Ladění vlastního ladicího stroje" je nutné počkat DE spuštění než budete moct připojit k němu. Pokud jste na začátku vaše DE, který se zobrazí při spuštění DE okno se zprávou, můžete připojit v daném okamžiku a zrušte zaškrtnutí pole zprávy pokračujte. Tímto způsobem můžete zachytit všechny DE události.  
  
> [!WARNING]
>  Musíte mít nainstalován předtím, než se pokusíte následující postupy vzdálené ladění. Zobrazit [vzdálené ladění](../../debugger/remote-debugging.md) podrobnosti.  
  
## <a name="debug-a-custom-debug-engine"></a>Ladění vlastního ladicího stroje  
  
1. Spustit *msvsmon.exe*, vzdálené ladění monitorování.  
  
2. Z **nástroje** v nabídce *msvsmon.exe*vyberte **možnosti** otevřít **možnosti** dialogové okno.  
  
3. Vyberte možnost "bez ověřování" a klikněte na tlačítko **OK**.  
  
4. Spustit instanci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a otevřete svůj vlastní projekt DE.  
  
5. Spusťte druhou instanci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a otevřete svůj vlastní projekt, který spustí DE (pro vývoj, obvykle je to v experimentální podregistru, který je nastavený při instalaci VSIP).  
  
6. V této druhé instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], načíst zdrojový soubor z vašich vlastních projektů a spusťte program k ladění. Chvíli počkejte, než aby DE k načtení, nebo počkejte, dokud nebude dosaženo zarážky.  
  
7. V první instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (s projektem DE), vyberte **připojit k procesu** z **ladění** nabídky.  
  
8. V **připojit k procesu** dialogovém okně Změnit **přenosu** k **vzdálený (nativní pouze bez ověřování)**.  
  
9. Změnit **kvalifikátor** na název vašeho počítače (Poznámka: historie položek, je proto třeba tento název zadat pouze jednou).  
  
10. V **procesy k dispozici** seznamu, vyberte instanci služby vaší DE, který je spuštěný a klikněte na tlačítko **připojit** tlačítko.  
  
11. Po ve vaší DE jste načetli symboly, umístěte zarážky v kódu DE.  
  
12. Pokaždé, když zastavte a restartujte ladění procesu, opakujte kroky 6 až 10.  
  
## <a name="debug-a-custom-project-type"></a>Ladění do vlastního typu projektu  
  
1. Spustit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] normální podregistru a zatížení projektu zadejte projekt (to je, zdroje pro váš typ projektu není instancí typu projektu).  
  
2. Otevřete vlastnosti projektu a přejděte **ladění** stránky. Pro **příkaz**, zadejte cestu k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí (ve výchozím nastavení je to *[jednotka]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3. Pro **argumenty příkazu**, typ `/rootsuffix exp` pro experimentální podregistru (vytvořené při instalaci VSIP).  
  
4. Klikněte na tlačítko **OK** změny uložte.  
  
5. Spustit projekt typu stisknutím kombinace kláves **F5**. Tím se spustí druhé instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6. V tomto okamžiku můžete umístit zarážky ve zdrojovém kódu typ projektu.  
  
7. V druhé instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], načíst nebo vytvořit novou instanci typu projektu. Při tvorbě nebo zatížení vaší může zarážky.  
  
8. Ladění vašeho typu projektu.  
  
9. Pokud budete chtít ladit proces spuštění Zavedenými, provedením kroků v postupu "Ladění vlastního ladicího stroje" připojení k vaší DE po jeho spuštění. To vám dává tři instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] systémem: jedno pro typ zdroje projektu, druhý pro typ instance projektu a třetí připojené k vaší DE.  
  
## <a name="see-also"></a>Viz také:  
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)