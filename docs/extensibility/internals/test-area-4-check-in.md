---
title: 'Testovací oblast 4: vrácení se změnami | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704578"
---
# <a name="test-area-4-check-in"></a>Testovací oblast 4: Vrácení se změnami
Tato testovací oblast modulu plug-in zdrojového ovládacího prvku pokrývá odeslání aktualizovaných položek do úložiště verzí prostřednictvím příkazu **vrácení se** změnami.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]V testovacích případech se používají následující cesty nabídky integrovaného vývojového prostředí.

##### <a name="check-in"></a>Přihlásit se:
 **Soubor**, **Správa zdrojového kódu**, **vrácení se změnami**.

 **Soubor**, **vrátit se změnami**.

 Místní nabídka, **vrátit se změnami**

## <a name="common-expected-behavior"></a>Obvyklé očekávané chování

- Projekty a soubory přidané do řešení nebo projektu pod správou zdrojových kódů se zobrazí v dialogovém okně **vrátit** se změnami a v okně **nedokončené vrácení se změnami** .

- Po vrácení se změnami se přidané položky zobrazí ve správě zdrojového kódu.

- Po vrácení se změnami jsou aktualizované položky ve Storu správně ve verzi.

## <a name="test-cases"></a>Testovací případy
 Níže jsou uvedené konkrétní testovací případy pro testovací oblast pro vrácení se změnami.

### <a name="case-4a-modified-items"></a>Případ 4a: upravené položky
 Popisuje použití akce vrácení se změnami k aktualizaci souboru v rámci správy zdrojového kódu, který byl změněn.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Upravený textový soubor, který je rezervován, pouze soubor se změnami (zaškrtávací políčko se**změnami** )|1. Vytvořte nový projekt s textovým souborem.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Prohlédněte si a upravte textový soubor.<br />4. Vraťte se změnami pomocí dialogového okna vrátit se změnami (**soubor**, Správa **zdrojového kódu**, **vrátit se změnami**).|Obvyklé očekávané chování.|
|Upravený textový soubor, který je rezervován, vrátit se změnami pouze do souboru (okno**čeká na vrácení se změnami** )|1. Vytvořte nový projekt s textovým souborem.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Prohlédněte si a upravte textový soubor.<br />4. Projděte si okno s **nedokončenými změnami** .|Obvyklé očekávané chování.|

### <a name="case-4b-adding-files"></a>Případ 4b: Přidání souborů
 Při přidávání souboru do projektu nebo položky do řešení se musí také změnit projekt nebo řešení. Proto je nadřazený soubor také rezervován a musí být vrácen se změnami, aby bylo možné dokončit sčítání.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Přidat textový soubor a vrátit se změnami vše (dialogové okno**vrátit se změnami** )|1. Vytvořte nový projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte do projektu textový soubor.<br />4. Pokud se zobrazí výzva, přijměte rezervaci projektu.<br />5. Vyberte řešení v **Průzkumník řešení**.<br />6. Vraťte se změnami v dialogovém okně **vrátit** se změnami.|Obvyklé očekávané chování.|
|Přidat textový soubor a vrátit se změnami vše (okno**čeká na vrácení se změnami** )|1. Vytvořte nový projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte do projektu textový soubor.<br />4. Pokud se zobrazí výzva, přijměte rezervaci projektu.<br />5. vrátit se změnami řešení z **nedokončených vrácení se změnami** do okna|Obvyklé očekávané chování|

### <a name="case-4c-adding-projects"></a>Případ 4C: Přidání projektů
 Při přidávání projektu do řešení se musí také změnit řešení. Proto je soubor řešení také rezervován a musí být vrácen se změnami, aby bylo možné dokončit sčítání.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Přidání projektu do prázdného řešení v rámci správy zdrojového kódu (**zaškrtávací políčko vrátit se** změnami)|1. Vytvořte prázdné řešení.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte nový projekt.<br />4. Pokud se zobrazí výzva, přijměte rezervaci řešení.<br />5. Vraťte se změnami v dialogovém okně **vrátit** se změnami.|Obvyklé očekávané chování.|
|Přidání projektu do prázdného řešení v rámci správy zdrojového kódu (okno**čeká na vrácení se změnami** )|1. Vytvořte prázdné řešení.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte nový projekt.<br />4. Pokud se zobrazí výzva, přijměte rezervaci řešení.<br />5. vrátit se změnami řešení z **nedokončených vrácení se změnami** do okna|Obvyklé očekávané chování.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
