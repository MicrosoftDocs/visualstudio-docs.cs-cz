---
title: 'Testovací oblasti 7: Sdílet | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa74d6ff2291288a1ca0e7f17a2edb1e126f222b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142465"
---
# <a name="test-area-7-share"></a>Testování oblasti 7: sdílené složky
Tato oblast testovací zahrnuje sdílení položky mezi umístěními prostřednictvím **sdílenou složku** příkaz.  
  
 Operace hhare je zřejmá duplikace soubory a složky položek mezi dva nebo více umístění v souboru řízení zdrojové hierarchie. Duplikace nedojde skutečně na serveru, ale uživatel naleznete v souboru stejné ve dvou nebo více vybraných umístěních. Při každé změně žádnému sdílené položky, se tyto změny ve všech jiných sdílené umístění.  
  
 Sdílení do složek, které funguje, když vyberete složku obsahující alespoň jeden soubor ve správě zdrojového kódu v ní. Příkaz sdílené složky je zakázán za následujících podmínek:  
  
-   Pokud do vybrané složky k prázdné složce.  
  
-   Pokud skutečné složka existuje, ale neobsahuje žádné zdrojové soubory ovládacího prvku.  
  
-   Pokud virtuální složka existuje, zda jsou soubory ve správě zdrojového kódu v ní nebo ne.  
  
-   Pokud je vzdálené lokality webového projektu.  
  
## <a name="command-menu-access"></a>Příkaz přístup do nabídky  
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovací případy.  
  
 Sdílené složky: **soubor**->**ovládací prvek zdroje**->**sdílené složky**.  
  
## <a name="expected-behavior"></a>Očekávané chování  
  
-   Sdílený soubor se zobrazí v sdílené umístění.  
  
-   Zobrazení v zdroj ovládacího prvku verze úložiště historie se dozvíte, jsou sdílené soubory.  
  
-   Úpravy sdílený soubor upraví obě umístění souboru.  
  
## <a name="test-cases"></a>Testovací případy  
 Níže jsou uvedeny konkrétní testovací případy oblasti testovací sdílené složky.  
  
|Akce|Kroky testů|Očekávané výsledky ověření|  
|------------|----------------|--------------------------------|  
|Sdílení souboru do jiného projektu načíst z jednoho načíst projektu ve správě zdrojového kódu|1.  Vytvořte nový projekt.<br />2.  Přidejte druhý projekt k řešení.<br />3.  Vytvořte soubor v druhé projektu s názvem, který se nenachází v první projekt.<br />4.  Přidáte řešení do správy zdrojového kódu.<br />5.  Vyberte první projekt.<br />6.  Otevřete **sdílené složky** dialogové okno (**soubor** -> **správy zdrojového kódu** -> **sdílenou složku**).<br />7.  Sdílení souboru z druhé projektu na první projekt.<br />8.  Přijměte **rezervovat** po zobrazení výzvy.|Běžné očekávané chování.|  
|Sdílet jeden projektu soubor|1.  Vytvořte nový projekt.<br />2.  Přidejte ji do správy zdrojového kódu.<br />3.  Zavřete řešení.<br />4.  Vytvořte druhý projekt (nové řešení.)<br />5.  Přidáte řešení do správy zdrojového kódu.<br />6.  Vyberte projekt.<br />7.  Otevřete **sdílené složky** dialogové okno (**soubor** -> **správy zdrojového kódu** -> **sdílenou složku**).<br />8.  Sdílení souboru z dříve přidané projektu do otevřeného projektu.<br />9. Přijměte **rezervovat** po zobrazení výzvy.|Běžné očekávané chování.|  
|Sdílení souboru není součástí projektu od správy zdrojového kódu v aktuálně načtených projektu|1.  Vytvořte nový projekt.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Přidání souboru do správy zdrojového kódu, který není součástí projektu nebo řešení.<br />4.  Vyberte projekt a otevřete **sdílené složky** dialogové okno (**soubor** -> **správy zdrojového kódu** -> **sdílenou složku**).<br />5.  Vyberte soubor v rámci **sdílet** dialogu, který neexistuje v aktuální projekt nebo řešení a sdílet ho.<br />6.  Přijměte **rezervovat** po zobrazení výzvy.|Zdrojové úložiště ovládacího prvku provedl Get, tak, že soubor je nyní v místním umístění projektu.|  
|Sdílení souborů v rámci stejného projektu do jiné složky|1.  Vyberte **automaticky rezervovat** v **nástroje** -> **možnosti** -> **správy zdrojového kódu**.<br />2.  Vytvoření nového projektu a přidat jej do správy zdrojového kódu.<br />3.  Přidáte složku do projektu.<br />4.  Přidá soubor do složky a zkontrolujte ve složce.<br />5.  Vyberte složku.<br />6.  Otevřete **sdílené složky** dialogové okno (**soubor** -> **správy zdrojového kódu** -> **sdílenou složku**).<br />7.  Sdílení souboru do vybrané složky.|Běžné očekávané chování.<br /><br /> Složky musí být kontrolované pomocí souboru v něm před použitím pro sdílenou složku.|  
|Sdílené složky do projektu načíst – rekurzivní|1.  Vytvořte nový projekt.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Vyberte projekt.<br />4.  Otevřete **sdílené složky** dialogové okno (**soubor** -> **správy zdrojového kódu** -> **sdílenou složku**).<br />5.  Vyberte složku.<br />6.  Sdílejte rekurzivní složky do projektu.|Běžné očekávané chování.|  
|Sdílet několik souborů z jedné projektu do jiného|1.  Vytvoření nového projektu s několik souborů v ní.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Zavřete řešení.<br />4.  Vytvořte nový projekt v nové řešení.<br />5.  Přidáte řešení do správy zdrojového kódu.<br />6.  Vyberte projekt.<br />7.  Otevřete **sdílené složky** dialogové okno (**soubor** -> **správy zdrojového kódu** -> **sdílenou složku**).<br />8.  Sdílejte několik souborů z dříve vytvořený projekt aktuálně otevřeného projektu.|Běžné očekávané chování.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)