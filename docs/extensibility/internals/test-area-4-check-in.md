---
title: 'Testovací oblast 4: Přihlášení | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704578"
---
# <a name="test-area-4-check-in"></a>Testovací oblast 4: Vrácení se změnami
Tato testovací oblast modulu plug-in správy zdrojového kódu zahrnuje odesílání aktualizovaných položek do úložiště verzí pomocí příkazu **Vrácení se změnami.**

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovacích případech.

##### <a name="check-in"></a>Přihlásit se:
 **Soubor**, **Řízení zdrojového kódu**, **Vrácení se změnami**.

 **Soubor**, **vrácení se změnami**.

 Místní nabídka, **vrácení se změnami**.

## <a name="common-expected-behavior"></a>Běžné očekávané chování

- Projekty a soubory přidané do řešení nebo projektu pod správou zdrojového kódu se zobrazí v dialogovém okně **Vrácení se změnami** a v okně **Čekající vrácení se změnami.**

- Po vrácení se změnami se v ovládacím prvku zdrojového kódu zobrazí přidané položky.

- Po vrácení se změnami jsou aktualizované položky správně verzí v obchodě.

## <a name="test-cases"></a>Testovací případy
 Následují specifické testovací případy pro testovací oblast vrácení se změnami.

### <a name="case-4a-modified-items"></a>Případ 4a: Upravené položky
 Popisuje použití akce vrácení se změnami k aktualizaci souboru pod správou zdrojového kódu, který byl změněn.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Změna textového souboru, který byl rezervován, pouze soubor se změnami (dialogové okno**Vrácení se změnami)**|1. Vytvořte nový projekt s textovým souborem.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Rezervovat a upravit textový soubor.<br />4. Vrácení se změnami pomocí dialogového okna Vrácení se změnami **(Soubor,** **Řízení zdrojového kódu**, **Vrácení se změnami).**|Společné očekávané chování.|
|Změna textového souboru, který byl rezervován, pouze soubor se změnami (okno**Čekající vrácení se změnami)**|1. Vytvořte nový projekt s textovým souborem.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Rezervovat a upravit textový soubor.<br />4. Přihlašte se pomocí okna **Čekající vrácení se změnami.**|Společné očekávané chování.|

### <a name="case-4b-adding-files"></a>Případ 4b: Přidávání souborů
 Při přidávání souboru do projektu nebo položky do řešení musí být projekt nebo řešení také změnit. Proto je nadřazený soubor také rezervován a musí být se změnami k dokončení přidání.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Přidání textového souboru a vrácení se změnami ve všem (dialogové okno**Se změnami)**|1. Vytvořte nový projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte textový soubor do projektu.<br />4. Přijměte check-out projektu, pokud je výzva.<br />5. Vyberte řešení v **Průzkumníku řešení**.<br />6. Vrácení se změnami z dialogového okna **Vrácení se změnami**|Společné očekávané chování.|
|Přidání textového souboru a vrácení se změnami ve všem (okno**Čekající vrácení se změnami)**|1. Vytvořte nový projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte textový soubor do projektu.<br />4. Přijměte check-out projektu, pokud je výzva.<br />5. Vrácení se změnami řešení z **okna Čekající vrácení se změnami.**|Běžné očekávané chování|

### <a name="case-4c-adding-projects"></a>Případ 4c: Přidání projektů
 Při přidávání projektu do řešení, řešení musí také změnit. Proto je soubor řešení také rezervován a musí být se změnami, aby bylo dokončeno přidání.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Přidání projektu do prázdného řešení pod správou zdrojového kódu (dialogové okno**Vrácení se změnami)**|1. Vytvořte prázdný roztok.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte nový projekt.<br />4. Přijměte check-out řešení, pokud je výzva.<br />5. Vrácení se změnami z dialogového okna **Vrácení se změnami**|Společné očekávané chování.|
|Přidání projektu do prázdného řešení pod správou zdrojového kódu (okno**Čekající vrácení se změnami)**|1. Vytvořte prázdný roztok.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte nový projekt.<br />4. Přijměte check-out řešení, pokud je výzva.<br />5. Vrácení se změnami řešení z **okna Čekající vrácení se změnami.**|Společné očekávané chování.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
