---
title: 'Test oblasti 4: Zkontrolujte v | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7f3e8a343823016f391735aae59e58dfefe1a5f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133122"
---
# <a name="test-area-4-check-in"></a>Test oblasti 4: Vrácení se změnami
Tato oblast modulu plug-in testovací zdrojového kódu zahrnuje odesílání aktualizované položky k úložišti verzí prostřednictvím **změnami** příkaz.  
  
## <a name="command-menu-access"></a>Příkaz přístup do nabídky  
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovací případy.  
  
##### <a name="check-in"></a>Přihlásit se:  
 **Soubor**, **ovládací prvek zdroje**, **změnami**.  
  
 **Soubor**, **změnami**.  
  
 Místní nabídky, **změnami**.  
  
## <a name="common-expected-behavior"></a>Běžné očekávané chování  
  
-   Projekty a soubory přidané do řešení nebo projektu ve správě zdrojového kódu se zobrazí v **změnami** dialogové okno a **čeká na vrácení se změnami** okno.  
  
-   Po změnami zobrazí přidané položky ve správě zdrojového kódu.  
  
-   Po této kontroly v jsou aktualizované položky správně verzí v úložišti.  
  
## <a name="test-cases"></a>Testovací případy  
 Níže jsou uvedeny konkrétní testovací případy oblasti testovací vrácení se změnami.  
  
### <a name="case-4a-modified-items"></a>Případ 4a: Upravit položky  
 Popisuje, pomocí kontroly v akci a aktualizovat soubor ve správě zdrojového kódu, která byla změněna.  
  
|Akce|Kroky testů|Očekávané výsledky ověření|  
|------------|----------------|--------------------------------|  
|Upravit textový soubor, který byl rezervován, zkontrolujte v souboru pouze (**změnami** dialogové okno)|1.  Vytvoření nového projektu pomocí textového souboru.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Rezervace a upravit textového souboru.<br />4.  Pomocí dialogového okna změnami se změnami (**soubor**, **správy zdrojového kódu**, **změnami**).|Běžné očekávané chování.|  
|Upravit textový soubor, který byl rezervován, zkontrolujte v souboru pouze (**čeká na vrácení se změnami** okna)|1.  Vytvoření nového projektu pomocí textového souboru.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Rezervace a upravit textového souboru.<br />4.  Zkontrolujte v prostřednictvím **čeká na vrácení se změnami** okno.|Běžné očekávané chování.|  
  
### <a name="case-4b-adding-files"></a>Případ 4b: přidávání souborů  
 Když přidáváte soubor do projektu nebo položku, kterou chcete řešení, projekt nebo řešení musí také změnit. Proto nadřazeném souboru je také rezervována a musí být pro dokončení přidání změnami.  
  
|Akce|Kroky testů|Očekávané výsledky ověření|  
|------------|----------------|--------------------------------|  
|Přidejte do textového souboru a všechno, co se změnami (**změnami** dialogové okno)|1.  Vytvořte nový projekt.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Do textového souboru přidejte do projektu.<br />4.  Podívejte se na projektu přijměte, pokud se zobrazí výzva.<br />5.  Vybrat řešení v **Průzkumníku řešení**.<br />6.  Zkontrolujte v z **změnami** dialogové okno.|Běžné očekávané chování.|  
|Přidejte do textového souboru a všechno, co se změnami (**čeká na vrácení se změnami** okna)|1.  Vytvořte nový projekt.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Do textového souboru přidejte do projektu.<br />4.  Podívejte se na projektu přijměte, pokud se zobrazí výzva.<br />5.  Zkontrolujte v řešení z **čeká na vrácení se změnami** okno.|Běžné očekávané chování|  
  
### <a name="case-4c-adding-projects"></a>Případ 4c: Přidání projektů  
 Při přidávání projektu do řešení, musíte změnit taky řešení. Proto soubor řešení je také rezervována a musí být pro dokončení přidání změnami.  
  
|Akce|Kroky testů|Očekávané výsledky ověření|  
|------------|----------------|--------------------------------|  
|Přidat projekt do prázdného řešení ve správě zdrojového kódu (**změnami** dialogové okno)|1.  Vytvoření prázdného řešení.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Přidáte nový projekt.<br />4.  Podívejte se na řešení přijměte, pokud se zobrazí výzva.<br />5.  Zkontrolujte v z **změnami** dialogové okno.|Běžné očekávané chování.|  
|Přidat projekt do prázdného řešení ve správě zdrojového kódu (**čeká na vrácení se změnami** okna)|1.  Vytvoření prázdného řešení.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Přidáte nový projekt.<br />4.  Podívejte se na řešení přijměte, pokud se zobrazí výzva.<br />5.  Zkontrolujte v řešení z **čeká na vrácení se změnami** okno.|Běžné očekávané chování.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)