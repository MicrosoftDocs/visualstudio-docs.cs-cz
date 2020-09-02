---
title: Zobrazit paměť pro proměnné v ladicím programu | Microsoft Docs
ms.custom: ''
ms.date: 10/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51070e06f684c2e873ded76ec8797ed7587745ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348317"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Použít paměťová okna v ladicím programu sady Visual Studio (C#, C++, Visual Basic, F #)

Během ladění zobrazuje okno **paměť** místo v paměti, které vaše aplikace používá.

Okna ladicího programu, jako jsou **kukátko**, **Automatické**hodnoty, **místní**hodnoty a dialog **QuickWatch** , zobrazují proměnné, které jsou uloženy v určitých umístěních v paměti. V okně **paměť** se zobrazí celkový obrázek. Zobrazení paměti je výhodné pro zkoumání velkých částí dat (například vyrovnávacích pamětí nebo velkých řetězců), které se v ostatních oknech nezobrazují dobře.

Okno **paměti** není omezené na zobrazení dat. Zobrazuje vše v paměťovém prostoru, včetně dat, kódu a náhodných bitů paměti v nepřiřazené paměti.

Okno **paměti** není k dispozici pro ladění skriptů nebo SQL. Tyto jazyky nerozpoznají koncept paměti.

## <a name="open-a-memory-window"></a>Otevřít okno paměti

Stejně jako ostatní okna ladicího programu jsou **paměťová** okna dostupná pouze během relace ladění.

>[!IMPORTANT]
>Chcete-li povolit okna **paměti** , **Povolte ladění na úrovni adres** , které je **Tools**nutné vybrat v  >  **možnostech** nástrojů (nebo **Debug**  >  **Možnosti**ladění) > **Debugging**  >  **Obecné**ladění.

**Otevření okna paměti**

1. Ujistěte se, že je vybrána možnost **Povolit ladění na úrovni adresy** v **Tools**  >  **možnostech** nástrojů (nebo **Debug**  >  **Možnosti**ladění) > **Debugging**  >  **Obecné**ladění.

1. Spusťte ladění tak, že vyberete zelenou šipku, stisknete klávesu **F5** **nebo vyberete ladění**  >  **Spustit ladění**.

2. V části **ladit**  >  **Windows**  >  **paměť**Windows vyberte **paměť 1**, **paměť 2**, **paměť 3**nebo **paměť 4**. (Některé edice [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nabídky nabízí jenom jedno okno **paměti** .)

## <a name="move-around-in-the-memory-window"></a>Pohyb v okně paměti

Adresní prostor počítače je velký a můžete ho snadno ztratit posouváním v okně **paměti** .

V dolní části okna se zobrazí vyšší adresy paměti. Pokud chcete zobrazit vyšší adresu, posuňte se dolů. Pokud chcete zobrazit nižší adresu, posuňte se nahoru.

V okně **paměti** můžete okamžitě přejít na zadanou adresu pomocí přetažení nebo zadáním adresy do pole **adresa** . Pole **adresa** přijímá alfanumerické adresy a výrazy, které se vyhodnotí jako adresy `e.User.NonroamableId` .

Chcete-li vynutit okamžité opakované vyhodnocení výrazu v poli **adresa** , vyberte ikonu **automaticky přehodnocení** .

Ve výchozím nastavení okno **paměti** zpracovává výrazy **adres** jako živé výrazy, které jsou znovu vyhodnocovány při spuštění aplikace. Živé výrazy mohou být užitečné, například pro zobrazení paměti, která je dotykem proměnné ukazatele.

**Přesunutí do umístění v paměti pomocí přetažení myší:**

1. V jakémkoli okně ladicího programu vyberte adresu paměti nebo proměnnou ukazatele obsahující adresu paměti.

2. Přetáhněte adresu nebo ukazatel v okně **paměti** . Tato adresa se pak zobrazí v poli **adresa** a v okně **paměť** se upraví na zobrazenou adresu v horní části.

**Pokud se chcete přesunout do umístění paměti tím, že ho zadáte do pole Adresa:**

- Zadejte nebo vložte adresu nebo výraz do pole **adresa** a stiskněte klávesu **ENTER**nebo vyberte v rozevíracím seznamu v poli **adresa** . Okno **paměť** se upraví tak, aby se zobrazila adresa v horní části.

## <a name="customize-the-memory-window"></a>Přizpůsobení okna paměti

Ve výchozím nastavení se obsah paměti zobrazuje jako celá čísla v šestnáctkovém formátu a šířka okna určuje počet zobrazených sloupců. Můžete upravit způsob, jakým okno **paměti** zobrazuje obsah paměti.

**Postup změny formátu obsahu paměti:**

- Pravým tlačítkem myši klikněte v okně **paměť** a v místní nabídce vyberte požadované formáty.

**Změna počtu sloupců v okně paměti:**

- Vyberte šipku rozevíracího seznamu vedle pole **sloupce** a vyberte počet sloupců, které chcete zobrazit, nebo vyberte možnost **automaticky** pro automatické úpravy podle šířky okna.

Pokud nechcete, aby se obsah okna **paměti** měnil při spuštění aplikace, můžete vyhodnotit Live Expression reevaluation.

**Postup při vypínání služby Live Evaluation:**

- Pravým tlačítkem myši klikněte v okně **paměť** a v místní nabídce vyberte znovu **automaticky vyhodnotit** .

  >[!NOTE]
  >Vyhodnocování živých výrazů je přepínací tlačítko a je standardně zapnuté, takže výběr **přehodnocení se automaticky** vypne. Opětovným výběrem možnosti znovu **vyhodnotit automaticky** znovu navrátit.

Panel nástrojů můžete skrýt nebo zobrazit v horní části okna **paměti** . Pokud je panel nástrojů skrytý, nebudete mít přístup k poli **adresa** nebo k jiným nástrojům.

**Přepnutí zobrazení panelu nástrojů:**

- Pravým tlačítkem myši klikněte v okně **paměť** a v místní nabídce vyberte **Zobrazit panel nástrojů** . Panel nástrojů se zobrazí nebo zmizí v závislosti na předchozím stavu.

## <a name="follow-a-pointer-through-memory"></a>Sledovat ukazatel paměti

V nativních aplikacích kódu můžete jako živé výrazy použít názvy registru. Například můžete použít ukazatel zásobníku a postupovat podle zásobníku.

**Postup při sledování ukazatele paměti:**

1. Do pole **adresa** v okně **paměti** zadejte výraz ukazatele, který se nachází v aktuálním oboru. V závislosti na jazyku bude pravděpodobně nutné na něj odkázat.

2.  Stiskněte **Enter**.

   Použijete-li příkaz ladění, jako je například **Krok**, adresa paměti zobrazená v poli **adresa** a v horní části okna **paměti** se automaticky změní při změně ukazatele.

## <a name="see-also"></a>Viz také
- [Zobrazit data v ladicím programu](../debugger/viewing-data-in-the-debugger.md)