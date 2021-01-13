---
title: Zobrazit vlákna v ladicím programu | Microsoft Docs
description: K prohlédnutí a řízení vláken použijte vlákna. Můžete seskupovat, řadit, označovat, zablokovat, rozmrazit a hledat vlákna, vybírat sloupce a zobrazovat zásobníky volání.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b02d980292eaed40c7c1598c772b52f695bf23e2
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149700"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Zobrazení vláken v ladicím programu sady Visual Studio pomocí okna vlákna (C#, Visual Basic, C++)
V okně **vlákna** můžete prozkoumávat a pracovat s vlákny v aplikaci, kterou ladíte. Podrobné pokyny týkající se použití okna **vlákna** naleznete v tématu [Návod: ladění pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Použití okna vláken
 Okno **vlákna** obsahuje tabulku, ve které každý řádek popisuje samostatné vlákno ve vaší aplikaci. Ve výchozím nastavení tabulka obsahuje seznam všech vláken v aplikaci, ale můžete filtrovat seznam, aby se zobrazila pouze vlákna, která vás zajímají. Každý sloupec popisuje jiný typ informací. Můžete také skrýt některé sloupce. Pokud zobrazíte všechny sloupce, zobrazí se následující sloupce zleva doprava:

- **Příznak**: v tomto neoznačeném sloupci můžete označit vlákno, ke kterému chcete věnovat zvláštní pozornost. Informace o tom, jak označit vlákno, naleznete v tématu [How to: flag and unflags](../debugger/how-to-flag-and-unflag-threads.md)Threads.

- **Aktuální vlákno**: v tomto neoznačeném sloupci se žlutá šipka označuje jako aktuální vlákno. Obrys šipky označuje aktuální kontext ladicího programu pro jiné než aktuální vlákno.

- **ID**: zobrazuje identifikační číslo pro každé vlákno.

- **MANAGED ID**: zobrazuje spravované identifikační čísla pro spravovaná vlákna.

- **Category**: Zobrazuje kategorii vláken buď jako vlákna uživatelského rozhraní, obslužné rutiny vzdálených volání procedur nebo pracovních vláken. Speciální kategorie identifikuje hlavní vlákno aplikace.

- **Name**: identifikuje každé vlákno podle názvu, pokud má jednu, nebo jako \<No Name> .

- **Umístění**: zobrazuje, kde je vlákno spuštěno. Můžete rozbalit toto umístění a zobrazit plný zásobník volání pro vlákno.

- **Priority**: rozšířený sloupec (skrytý ve výchozím nastavení), který zobrazuje prioritu nebo prioritu, kterou systém přiřadil jednotlivým vláknům.

- **Maska spřažení**: rozšířený sloupec (skrytý ve výchozím nastavení), který zobrazuje masku spřažení procesoru pro každé vlákno. V systému s více procesory určuje maska spřažení procesory, ve kterých může být vlákno spuštěno.

- **Počet pozastavených**: rozšířený sloupec (ve výchozím nastavení skrytý), který zobrazuje počet pozastavených. Tento počet Určuje, zda může být vlákno spuštěno. Další informace o pozastavených počítáních naleznete v tématu rozmrazit [a uvolnit vlákna](#freeze-and-thaw-threads).

- **Název procesu**: rozšířený sloupec (skrytý ve výchozím nastavení), který zobrazuje proces, ke kterému patří každé vlákno. Data v tomto sloupci mohou být užitečná při ladění mnoha procesů.

- **ID procesu**: rozšířený sloupec (skrytý ve výchozím nastavení), který zobrazuje ID procesu, ke kterému patří každé vlákno.

- **Kvalifikátor přenosu**: rozšířený sloupec (skrytý ve výchozím nastavení), který jednoznačně identifikuje počítač, ke kterému je připojen ladicí program.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Zobrazení okna vlákna v režimu pozastavení nebo režimu spuštění

- Když je Visual Studio v režimu ladění, vyberte nabídku **ladění** , přejděte na **Windows** a pak vyberte **vlákna**.

### <a name="to-display-or-hide-a-column"></a>Zobrazení nebo skrytí sloupce

- Na panelu nástrojů v horní části okna **vlákna** vyberte **sloupce**. Pak vyberte nebo zrušte název sloupce, který chcete zobrazit nebo skrýt.

## <a name="display-flagged-threads"></a>Zobrazit vlákna označená příznakem
 Můžete označit vlákno, které chcete poskytnout zvláštní pozornost, a to tak, že ho označíte ikonou v okně **vlákna** . Další informace naleznete v tématu [How to: Flags and unflags Threads](../debugger/how-to-flag-and-unflag-threads.md). V okně **vlákna** se můžete rozhodnout zobrazit všechna vlákna nebo pouze vlákna označená příznakem.

### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem

- V horní části okna **vlákna** vyberte možnost **Zobrazit vlákna označená příznakem pouze** na panelu nástrojů. (Pokud je neaktivní, budete muset nejprve označit některá vlákna.)

## <a name="freeze-and-thaw-threads"></a>Zablokovat a uvolnit vlákna
 Při zablokování vlákna systém nespustí provádění vlákna, i když jsou prostředky k dispozici.

 V nativním kódu můžete pozastavit nebo obnovit vlákna voláním funkcí systému Windows `SuspendThread` a `ResumeThread` . Nebo zavolejte funkce MFC [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) a [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Pokud zavoláte `SuspendThread` nebo `ResumeThread` , *pozastavený počet* zobrazený v okně **vlákna** bude změněn. Počet pozastavených se nemění, pokud zabráníte nebo odmrazete nativní vlákno. Vlákno nemůže být spuštěno v nativním kódu, pokud není odmrazení a má pozastavený počet nula.

 Ve spravovaném kódu se počet pozastavených změn změní při zmrazení nebo odblokování vlákna. Pokud dojde ke zmrazení vlákna ve spravovaném kódu, jeho počet pozastavených je 1. Při zablokování vlákna v nativním kódu je jeho počet pozastaveno 0, pokud jste volání nepoužili `SuspendThread` .

> [!NOTE]
> Při ladění volání z nativního kódu do spravovaného kódu je spravovaný kód spuštěn ve stejném fyzickém vlákně jako nativní kód, který jej volal. Pozastavení nebo zmrazení nativního vlákna zablokuje také spravovaný kód.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Zablokování nebo odmrazení spuštění vlákna

- Na panelu nástrojů v horní části okna **vlákna** vyberte možnost **ukotvit vlákna** nebo **uvolnit vlákna**.

     Tato akce ovlivní pouze vlákna, která jsou vybrána v okně **vlákna** .

### <a name="switch-to-another-thread"></a>Přepnout na jiné vlákno

Žlutá šipka indikuje aktuální vlákno (a umístění ukazatele provádění). Zelená šipka s kudrlinkou zakončením označuje, že neaktuální vlákno má aktuální kontext ladicího programu.

#### <a name="to-switch-to-another-thread"></a>Přepnutí na jiné vlákno

- Proveďte jeden z následujících kroků:

  - Dvakrát klikněte na jakékoli vlákno.

  - Klikněte pravým tlačítkem na vlákno a vyberte **Přepnout do vlákna**.

## <a name="group-and-sort-threads"></a>Seskupit a seřadit vlákna
 Při seskupování vláken se v tabulce zobrazí záhlaví pro každou skupinu. Nadpis obsahuje popis skupiny, například **pracovní vlákno** nebo **neoznačená vlákna** a ovládací prvek stromu. Členská vlákna každé skupiny se zobrazí pod záhlavím skupiny. Chcete-li skrýt členské vlákna pro skupinu, použijte ovládací prvek strom pro sbalení skupiny.

 Vzhledem k tomu, že seskupování mají přednost před řazením, můžete seskupit vlákna podle kategorií, například a seřadit je podle ID v rámci každé kategorie.

### <a name="to-sort-threads"></a>Řazení vláken

1. Na panelu nástrojů v horní části okna **vlákna** vyberte tlačítko v horní části libovolného sloupce.

     Vlákna jsou nyní seřazena podle hodnot v tomto sloupci.

2. Chcete-li změnit pořadí řazení, znovu vyberte stejné tlačítko.

     Vlákna, která se objevila v horní části seznamu, se teď zobrazují dole.

### <a name="to-group-threads"></a>Seskupení vláken

- Na panelu nástrojů okna **vlákna** vyberte seznam **Seskupit podle** a pak vyberte kritéria, podle kterých chcete seskupit vlákna.

### <a name="to-sort-threads-within-groups"></a>Řazení vláken v rámci skupin

1. Na panelu nástrojů v horní části okna **vlákna** vyberte seznam **Group by (seskupit podle** ) a pak vyberte kritéria, podle kterých chcete seskupit vlákna.

2. V okně **vlákna** vyberte tlačítko v horní části libovolného sloupce.

     Vlákna jsou nyní seřazena podle hodnot v tomto sloupci.

### <a name="to-expand-or-collapse-all-groups"></a>Chcete-li rozbalit nebo sbalit všechny skupiny

- Na panelu nástrojů v horní části okna **vlákna** vyberte **Rozbalit skupiny** nebo **sbalit skupiny**.

## <a name="search-for-specific-threads"></a>Vyhledat konkrétní vlákna
 Můžete vyhledat vlákna, která odpovídají zadanému řetězci v okně **vlákna** . Při hledání vláken v okně se zobrazí všechna vlákna, která odpovídají hledanému řetězci v jakémkoli sloupci. Tyto informace zahrnují umístění vlákna, které se zobrazí v horní části zásobníku volání ve sloupci **umístění** . Ve výchozím nastavení se neprohledávají úplný zásobník volání.

### <a name="to-search-for-specific-threads"></a>Hledání konkrétních vláken

1. Na panelu nástrojů v horní části okna **vlákna** klikněte do **vyhledávacího** pole a buď na:

     - Zadejte hledaný řetězec a stiskněte klávesu **ENTER**.

     \- ani

     - Vyberte rozevírací seznam vedle pole **hledání** a vyberte hledaný řetězec z předchozího hledání.

2. Volitelné Chcete-li do hledání zahrnout plný zásobník volání, vyberte možnost **zásobník volání vyhledávání**.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Zobrazení zásobníků volání vlákna a přepínání mezi snímky
V programu s více vlákny má každé vlákno vlastní zásobník volání. Okno **vlákna** nabízí pohodlný způsob, jak tyto zásobníky zobrazit.

> [!TIP]
> Pro vizuální znázornění zásobníku volání pro každé vlákno použijte okno [paralelní zásobníky](../debugger/get-started-debugging-multithreaded-apps.md) .

### <a name="to-view-the-call-stack-of-a-thread"></a>Zobrazení zásobníku volání vlákna

- Ve sloupci **umístění** vyberte opačný trojúhelník vedle umístění vlákna.

     Umístění rozbalí pro zobrazení zásobníku volání pro vlákno.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Zobrazení nebo sbalení zásobníků volání všech vláken

- Na panelu nástrojů v horní části okna **vlákna** vyberte možnost **Rozbalit zásobníky volání** nebo **sbalit zásobníky volání**.

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md)
