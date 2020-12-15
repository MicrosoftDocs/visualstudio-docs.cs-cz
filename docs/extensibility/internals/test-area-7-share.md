---
title: 'Testovací oblast 7: sdílení | Microsoft Docs'
description: Tato testovací oblast zdrojového kódu pokrývá sdílení položek mezi umístěními pomocí příkazu sdílení pro modul plug-in správy zdrojových kódů v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02593af854a9e68e7f4a6cc66f54452d3c3d3f94
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487605"
---
# <a name="test-area-7-share"></a>Testovací oblast 7: Sdílet
Tato testovací oblast pokrývá sdílení položek mezi umístěními prostřednictvím příkazu **share** .

 Operace Hhare je zjevné duplikace souborů a položek složky mezi dvěma nebo více umístěními v rámci hierarchie souborů správy zdrojového kódu. Duplikace na serveru neproběhne, ale uživatel uvidí stejný soubor ve dvou nebo více zadaných umístěních. Pokaždé, když se změny provedou u libovolné sdílené položky, tyto změny se zobrazí ve všech ostatních sdílených umístěních.

 Sdílení do složek funguje při výběru složky s alespoň jedním souborem v rámci správy zdrojového kódu. Příkaz Share je zakázaný za následujících podmínek:

- Pokud je vybraná složka prázdná složka.

- Pokud je k dispozici skutečná složka, ale neobsahuje žádné soubory správy zdrojového kódu.

- Pokud je k dispozici virtuální složka, zda jsou v ní soubory pod správou zdrojových kódů.

- Pokud je k dispozici webový projekt vzdálené lokality.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]V testovacích případech se používají následující cesty nabídky integrovaného vývojového prostředí.

 Share:  ->  -> **sdílená složka** správy zdrojového souboru.

## <a name="expected-behavior"></a>Očekávané chování

- Sdílený soubor se zobrazí ve sdíleném umístění.

- Zobrazení historie úložiště verzí správy zdrojového kódu ukazuje, že soubory jsou sdílené.

- Úpravou sdíleného souboru se upraví obě umístění souboru.

## <a name="test-cases"></a>Testovací případy
 Níže jsou uvedené konkrétní testovací případy pro oblast testování sdílení.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Sdílení souboru z jednoho načteného projektu v rámci správy zdrojového kódu do jiného načteného projektu|1. Vytvořte nový projekt.<br />2. Přidejte do řešení druhý projekt.<br />3. v druhém projektu vytvořte soubor s názvem, který není v prvním projektu.<br />4. Přidejte řešení do správy zdrojového kódu.<br />5. Vyberte první projekt.<br />6. Otevřete dialogové okno **sdílet** (  ->    ->  **sdílená složka** správy zdrojového kódu).<br />7. Sdílejte soubor od druhého projektu k prvnímu projektu.<br />8. Pokud se zobrazí výzva, přijměte **rezervaci** .|Obvyklé očekávané chování.|
|Sdílení souboru z jednoho projektu do druhého|1. Vytvořte nový projekt.<br />2. přidejte ho do správy zdrojového kódu.<br />3. Zavřete řešení.<br />4. Vytvořte druhý projekt (nové řešení).<br />5. Přidejte řešení do správy zdrojového kódu.<br />6. Vyberte projekt.<br />7. Otevřete dialogové okno **sdílet** (  ->    ->  **sdílená složka** správy zdrojových souborů).<br />8. Sdílejte soubor z dříve přidaného projektu k otevřenému projektu.<br />9. Pokud se zobrazí výzva, přijměte **rezervaci** .|Obvyklé očekávané chování.|
|Sdílet soubor, který není součástí projektu ze správy zdrojového kódu, do aktuálně načteného projektu|1. Vytvořte nový projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte soubor do správy zdrojového kódu, který není součástí projektu nebo řešení.<br />4. Vyberte projekt a otevřete dialogové okno **sdílet** (  ->    ->  **sdílená složka** správy zdrojových souborů).<br />5. Vyberte soubor v dialogovém okně **sdílet** , které neexistuje v aktuálním projektu nebo řešení a sdílejte ho.<br />6. Pokud se zobrazí výzva, přijměte **rezervaci** .|Úložiště správy zdrojů provedlo získání, takže soubor je nyní v místním umístění projektu.|
|Sdílet soubory v rámci stejného projektu s jinou složkou|1. v **nabídce nástroje**   ->  **Možnosti**  ->  **správy zdrojového kódu** vyberte možnost automaticky rezervovat.<br />2. Vytvořte nový projekt a přidejte ho do správy zdrojového kódu.<br />3. Přidejte do projektu složku.<br />4. Přidejte soubor do složky a vraťte se do složky.<br />5. Vyberte složku.<br />6. Otevřete dialogové okno **sdílet** (  ->    ->  **sdílená složka** správy zdrojového kódu).<br />7. Sdílejte soubor do vybrané složky.|Obvyklé očekávané chování.<br /><br /> Aby bylo možné složku použít ke sdílení, musí být v ní zaregistrovaná se souborem.|
|Sdílení složky do načteného projektu – rekurzivní|1. Vytvořte nový projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Vyberte projekt.<br />4. Otevřete dialogové okno **sdílet** (  ->    ->  **sdílená složka** správy zdrojových souborů).<br />5. Vyberte složku.<br />6. Sdílejte složku rekurzivně do projektu.|Obvyklé očekávané chování.|
|Sdílení několika souborů z jednoho projektu do druhého|1. Vytvořte nový projekt s několika soubory.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Zavřete řešení.<br />4. Vytvořte nový projekt v novém řešení.<br />5. Přidejte řešení do správy zdrojového kódu.<br />6. Vyberte projekt.<br />7. Otevřete dialogové okno **sdílet** (  ->    ->  **sdílená složka** správy zdrojových souborů).<br />8. Sdílejte několik souborů z dříve vytvořeného projektu do aktuálně otevřeného projektu.|Obvyklé očekávané chování.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
