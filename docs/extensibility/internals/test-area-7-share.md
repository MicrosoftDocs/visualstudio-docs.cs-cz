---
title: 'Testovací oblast 7: Podíl | Dokumenty společnosti Microsoft'
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
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704409"
---
# <a name="test-area-7-share"></a>Testovací oblast 7: Sdílení
Tato testovací oblast zahrnuje sdílení položek mezi umístěními pomocí příkazu **Sdílet.**

 Operace hhare je zdánlivá duplikace souborů a položek složek mezi dvěma nebo více umístěními v hierarchii souborů správy zdrojového kódu. Duplikace se ve skutečnosti nevyskytuje na serveru, ale uživatel vidí stejný soubor ve dvou nebo více určených umístěních. Při všech změnách v některé ze sdílených položek se tyto změny zobrazí ve všech ostatních sdílených umístěních.

 Sdílení do složek funguje, pokud vyberete složku s alespoň jedním souborem pod správu zdrojového kódu. Příkaz sdílení je zakázán za následujících podmínek:

- Pokud je vybraná složka prázdná složka.

- Pokud existuje skutečná složka, ale neobsahuje žádné soubory správy zdrojového kódu.

- Pokud existuje virtuální složka, zda jsou v ní soubory pod správu zdrojového kódu nebo ne.

- Pokud existuje webový projekt vzdáleného webu.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovacích případech.

 Sdílená složka: Sdílení**správy zdrojového kódu**-> **souboru**->.**Share**

## <a name="expected-behavior"></a>Očekávané chování

- Sdílený soubor se zobrazí ve sdíleném umístění.

- Zobrazení historie úložiště verzí správy zdrojového kódu ukazuje, že soubory jsou sdíleny.

- Úprava sdíleného souboru upravuje obě umístění souboru.

## <a name="test-cases"></a>Testovací případy
 Následují konkrétní testovací případy pro oblast testu sdílení.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Sdílení souboru z jednoho načteného projektu pod správou zdrojového kódu do jiného načteného projektu|1. Vytvořte nový projekt.<br />2. Přidejte druhý projekt do řešení.<br />3. Vytvořte soubor v druhém projektu s názvem, který není v prvním projektu.<br />4. Přidejte řešení do správy zdrojového kódu.<br />5. Vyberte první projekt.<br />6. Otevřít dialogové**Share**okno **Sdílení** (Sdílení správy**zdrojového kódu).** -> **Source Control** -> <br />7. Sdílejte soubor z druhého projektu do prvního projektu.<br />8. Přijmout **check-out,** pokud se zobrazí výzva.|Společné očekávané chování.|
|Sdílení souboru z jednoho projektu do druhého|1. Vytvořte nový projekt.<br />2. Přidejte jej do správy zdrojového kódu.<br />3. Uzavřete roztok.<br />4. Vytvořte druhý projekt (nové řešení.)<br />5. Přidejte řešení do správy zdrojového kódu.<br />6. Vyberte projekt.<br />7. Otevřete dialogové okno **Sdílet**  -> **(Sdílení****správy zdrojového****kódu).** -> <br />8. Sdílejte soubor z dříve přidaného projektu do otevřeného projektu.<br />9. Přijmout **check-out,** pokud se zobrazí výzva.|Společné očekávané chování.|
|Sdílení souboru, který není součástí projektu ze správy zdrojového kódu, do aktuálně načteného projektu|1. Vytvořte nový projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte soubor do správy zdrojového kódu, který není součástí projektu nebo řešení.<br />4. Vyberte projekt a otevřete dialogové okno **Sdílet** **(Sdílení****zdrojového** -> **kódu).** -> <br />5. Vyberte soubor v dialogovém okně **Sdílet,** který v aktuálním projektu nebo řešení neexistuje, a sdílejte jej.<br />6. Přijmout **check-out,** pokud se zobrazí výzva.|Úložiště správy zdrojového kódu provedlo get, takže soubor je nyní v místním umístění projektu.|
|Sdílení souborů v rámci stejného projektu do jiné složky|1. Vyberte **automaticky rezervovat** v **nástroji** -> **Možnosti** -> **Zdroj ové řízení**.<br />2. Vytvořte nový projekt a přidejte jej do správy zdrojového kódu.<br />3. Přidejte složku do projektu.<br />4. Přidejte soubor do složky a zaškrtávejte složku se změnami.<br />5. Vyberte složku.<br />6. Otevřít dialogové**Share**okno **Sdílení** (Sdílení správy**zdrojového kódu).** -> **Source Control** -> <br />7. Sdílení souboru do vybrané složky.|Společné očekávané chování.<br /><br /> Před použitím ke sdílení musí být složka se souborem se změnami.|
|Sdílení složky do načteného projektu – rekurzivní|1. Vytvořte nový projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Vyberte projekt.<br />4. Otevřete dialogové okno **Sdílet**  -> **(Sdílení****správy zdrojového****kódu).** -> <br />5. Vyberte složku.<br />6. Sdílejte složku rekurzivně do projektu.|Společné očekávané chování.|
|Sdílení několika souborů z jednoho projektu do druhého|1. Vytvořte nový projekt s několika soubory v něm.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Uzavřete roztok.<br />4. Vytvořte nový projekt v novém řešení.<br />5. Přidejte řešení do správy zdrojového kódu.<br />6. Vyberte projekt.<br />7. Otevřete dialogové okno **Sdílet**  -> **(Sdílení****správy zdrojového****kódu).** -> <br />8. Sdílejte několik souborů z dříve vytvořeného projektu do aktuálně otevřeného projektu.|Společné očekávané chování.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
