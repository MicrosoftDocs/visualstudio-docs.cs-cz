---
title: 'Testovací oblast 7: Sdílení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e9389d03da7c4e4b763e979a721a22639ecb9fbe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796919"
---
# <a name="test-area-7-share"></a>Testovací oblast 7: Sdílení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tento test oblast obsahuje informace o sdílení položek mezi umístěními prostřednictvím **sdílené složky** příkazu.  
  
 Operace hhare je zřejmý duplicitní soubory a složky položky mezi dva nebo více umístění v rámci zdrojové hierarchie soubor ovládacího prvku. Duplikace nedojde ve skutečnosti na serveru, ale uživatel zobrazit stejný soubor ve dvou nebo více zadaných umístění. Pokaždé, když dojde ke změně některou ze sdílené položky, se tyto změny ve všech jiných sdílené umístění.  
  
 Sdílení do složek, které funguje, pokud vyberete složku s alespoň jeden soubor pod správou zdrojových kódů v ní. Příkaz Sdílená složka je zakázán za následujících podmínek:  
  
-   Pokud se do vybrané složky je prázdné složce.  
  
-   Pokud je skutečná složka, ale neobsahuje žádné zdrojové soubory ovládacího prvku.  
  
-   Pokud existuje virtuální složka, jestli jsou soubory pod správou zdrojových kódů v ní nebo ne.  
  
-   Pokud je vzdálené lokality webového projektu.  
  
## <a name="command-menu-access"></a>Přístup do příkazu nabídky  
 Následující [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí nabídky cesty se používají v testovacích procesech.  
  
 Sdílené složky: **souboru**->**správy zdrojového kódu**->**sdílené složky**.  
  
## <a name="expected-behavior"></a>Očekávané chování  
  
-   Sdílený soubor se zobrazí ve sdíleném umístění.  
  
-   Zobrazení zdroje ovládací prvek verze úložiště historie zobrazí, že jsou sdílené soubory.  
  
-   Úpravy sdílený soubor upravuje i umístění souboru.  
  
## <a name="test-cases"></a>Testovací případy  
 Tady jsou konkrétní testovací případy pro oblasti testovací sdílené složky.  
  
|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Sdílení souboru na jiný projekt načíst z jednoho načtený projekt pod správou zdrojových kódů|1.  Vytvořte nový projekt.<br />2.  Přidáte druhý projekt do řešení.<br />3.  Vytvořte soubor v druhé projektu s názvem, který se nenachází v první projekt.<br />4.  Přidáte řešení do správy zdrojového kódu.<br />5.  Vyberte první projekt.<br />6.  Otevřít **sdílenou složku** dialogové okno (**souboru** -> **správy zdrojových kódů** -> **sdílené složky**).<br />7.  Sdílení souboru z druhého projektu do prvního projektu.<br />8.  Přijměte **rezervovat** Pokud se zobrazí výzva.|Běžné očekávané chování.|  
|Sdílení souboru z jednoho projektu do druhého|1.  Vytvořte nový projekt.<br />2.  Přidáte do správy zdrojového kódu.<br />3.  Zavřete řešení.<br />4.  Vytvořte druhý projekt (nové řešení.)<br />5.  Přidáte řešení do správy zdrojového kódu.<br />6.  Vyberte projekt.<br />7.  Otevřít **sdílenou složku** dialogové okno (**souboru** -> **správy zdrojových kódů** -> **sdílené složky**).<br />8.  Sdílení souboru z projektu dříve přidanými do otevřeného projektu.<br />9. Přijměte **rezervovat** Pokud se zobrazí výzva.|Běžné očekávané chování.|  
|Sdílení souboru není součástí projektu ze správy zdrojového kódu do právě načtený projekt|1.  Vytvořte nový projekt.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Přidejte soubor do správy zdrojového kódu, který není součástí projektu nebo řešení.<br />4.  Vyberte projekt a otevřete **sdílenou složku** dialogové okno (**souboru** -> **správy zdrojových kódů** -> **sdílené složky**).<br />5.  Vyberte soubor v rámci **sdílet** dialogové okno, které neexistuje v aktuálním projektu nebo řešení a sdílet ho.<br />6.  Přijměte **rezervovat** Pokud se zobrazí výzva.|Úložiště správy zdrojových kódů provedl Get, takže teď je soubor na místní umístění projektu.|  
|Sdílení souborů v rámci jednoho projektu do jiné složky|1.  Vyberte **zaregistrovat automaticky** v **nástroje** -> **možnosti** -> **správy zdrojových kódů**.<br />2.  Vytvořte nový projekt a přidat do správy zdrojového kódu.<br />3.  Přidáte složku do projektu.<br />4.  Přidejte soubor do složky a vrátit se změnami složku.<br />5.  Vyberte složku.<br />6.  Otevřít **sdílenou složku** dialogové okno (**souboru** -> **správy zdrojových kódů** -> **sdílené složky**).<br />7.  Sdílet soubor do vybrané složky.|Běžné očekávané chování.<br /><br /> Složka musí být kontrolované pomocí souboru v něm předtím, než je možné pro sdílenou složku.|  
|Sdílené složky do načtený projekt – rekurzivní|1.  Vytvořte nový projekt.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Vyberte projekt.<br />4.  Otevřít **sdílenou složku** dialogové okno (**souboru** -> **správy zdrojových kódů** -> **sdílené složky**).<br />5.  Vyberte složku.<br />6.  Sdílení složky rekurzivně do projektu.|Běžné očekávané chování.|  
|Sdílení několik souborů z jednoho projektu do druhého|1.  Vytvoření nového projektu s několika souborů.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Zavřete řešení.<br />4.  Vytvořte nový projekt v novém řešení.<br />5.  Přidáte řešení do správy zdrojového kódu.<br />6.  Vyberte projekt.<br />7.  Otevřít **sdílenou složku** dialogové okno (**souboru** -> **správy zdrojových kódů** -> **sdílené složky**).<br />8.  Sdílení několik souborů z dříve vytvořeném projektu do aktuálně otevřeného projektu.|Běžné očekávané chování.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

