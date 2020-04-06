---
title: 'Postup: Ladění vlastního ladicího modulu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738588"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Postup: Ladění vlastního ladicího modulu
Typ projektu spustí ladicí modul (DE) z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody. To znamená, že DE je spuštěn pod [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kontrolou instance řízení typu projektu. Tato instance však [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nelze ladit DE. Následuje postup, který umožňuje ladit vlastní DE.

> [!NOTE]
> : V postupu "Ladění vlastního ladicího stroje" musíte počkat, než se k němu de spustí. Pokud umístíte okno se zprávou v blízkosti začátku de, který se zobrazí při spuštění DE, můžete připojit v tomto okamžiku a zrušte zaškrtnutí maského okna pokračovat. Tímto způsobem můžete zachytit všechny události DE.

> [!WARNING]
> Před pokusem o následující postupy je nutné nainstalovat vzdálené ladění. Podrobnosti najdete [v tématu Vzdálené ladění.](../../debugger/remote-debugging.md)

## <a name="debug-a-custom-debug-engine"></a>Ladění vlastního ladicího stroje

1. Spusťte *nástroj msvsmon.exe*, vzdálený monitor ladění.

2. V nabídce **Nástroje** v *souboru msvsmon.exe*vyberte **Možnosti** a otevřete dialogové okno **Volby.**

3. Vyberte možnost "žádné ověřování" a klepněte na tlačítko **OK**.

4. Spusťte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instanci a otevřete vlastní projekt DE.

5. Spusťte druhou [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instanci a otevřete vlastní projekt, který spustí DE (pro vývoj, to je obvykle v podregistru experimentální registru, který je nastaven při instalaci VSIP).

6. V této druhé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instanci načíst zdrojový soubor z vlastního projektu a spustit program, který má být laděn. Počkejte několik okamžiků, aby DE načíst nebo počkejte, dokud je přístupů zarážka.

7. V první instanci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (s de projektu) vyberte připojit k **procesu** z nabídky **ladění.**

8. V dialogovém okně **Připojit k procesu** změňte **přenos** na **vzdálený (nativní pouze bez ověřování).**

9. Změňte **kvalifikátor** na název počítače (poznámka: existuje historie položek, takže tento název je třeba zadat pouze jednou).

10. V seznamu **Dostupné procesy** vyberte instanci de, která je spuštěna, a klepněte na tlačítko **Připojit.**

11. Po načtení symbolů ve vašem DE umístěte zarážky v kódu DE.

12. Pokaždé, když zastavíte a restartujete proces ladění, opakujte kroky 6 až 10.

## <a name="debug-a-custom-project-type"></a>Ladění vlastního typu projektu

1. Začněte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v podregistru normální registru a načtěte projekt typu projektu (toto je zdroj pro typ projektu, nikoli instance typu projektu).

2. Otevřete vlastnosti projektu a přejděte na stránku **Ladění.** Příkaz **emitován**zadejte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cestu k rozhraní IDE (ve výchozím nastavení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se jedná o soubor *[drive]* \Program Files\Microsoft 8\Common7\IDE\devenv.exe).

3. Pro **argumenty příkazu**zadejte `/rootsuffix exp` podregistr experimentálního registru (vytvořený při instalaci VSIP).

4. Klepnutím na **tlačítko OK** změny přijmete.

5. Začněte s typem projektu stisknutím **klávesy F5**. Tím se spustí druhá [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instance .

6. V tomto okamžiku můžete umístit zarážky ve zdrojovém kódu typu projektu.

7. Ve druhé instanci aplikace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]načtěte nebo vytvořte novou instanci typu projektu. Během načítání nebo vytváření může být přístupů zarážky.

8. Ladění typu projektu.

9. Pokud se rozhodnete ladit proces spouštění DE, můžete provést kroky v postupu "Ladění vlastního ladicího stroje", který se připojí k de po jeho spuštění. To vám dává tři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instance spuštění: jeden pro zdroj typu projektu, druhý pro typ instance projektu a třetí připojené k DE.

## <a name="see-also"></a>Viz také
- [Vytvoření vlastního ladicího modulu](../../extensibility/debugger/creating-a-custom-debug-engine.md)
