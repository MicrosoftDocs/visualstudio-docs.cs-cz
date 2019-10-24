---
title: O okně Registry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4deaf03013b6e28ea02e6ec7412bd23a05f1b87e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738254"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>O okně Registry v aplikaci Visual Studio (C#, C++, Visual Basic, F#)

Okno **Registry** je k dispozici pouze v případě, že je povoleno ladění na úrovni adresy v dialogovém okně **Možnosti** , uzel **ladění** .

 Registry jsou speciální umístění v rámci procesoru (CPU), která se používají k ukládání malých částí dat, na kterých procesor aktivně pracuje. Kompilování nebo interpretace zdrojového kódu vygeneruje pokyny, které přesouvají data z paměti do registrů a znovu zpět, podle potřeby. Přístup k datům v registrech je velmi rychlý v porovnání s přístupem k datům v paměti, takže kód, který umožňuje procesoru uchovávat data v registru, a k opakovanému přístupu má za následek rychlejší spouštění, než je kód, který vyžaduje, aby procesor mohl průběžně načítat a uvolňovat Registry. Aby mohla kompilátor uchovávat data v registrech a provádět další optimalizace, měli byste se vyhnout použití globálních proměnných a co nejvíc spoléhat na místní proměnné. Kód psaný tímto způsobem je označován jako dobrá místní reference. V některých jazycích, jako je například CC++/, programátor může deklarovat proměnnou registru, která instruuje kompilátor, aby si vyzkoušel, že by měla být proměnná v registru pokaždé. Další informace najdete v tématu věnovaném [klíčovému slovu Register](https://msdn.microsoft.com/library/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).

 Registry lze rozdělit do dvou typů: pro obecné účely a zvláštní účely. Registry pro obecné účely uchovávají data pro obecné operace, jako je například přidání dvou čísel dohromady nebo odkazování na prvek v poli. Registry pro zvláštní účely mají specifické účely a specializované významy. Dobrým příkladem je registr ukazatele na zásobníku, který procesor používá ke sledování zásobníku volání programu. Jako programátor nebudete pravděpodobně chtít manipulovat ukazatelem zásobníku přímo. Je však nezbytné správné fungování programu, protože bez ukazatele zásobníku by procesor neznal, kde se má vrátit na konci volání funkce.

 Většina registrací pro obecné účely drží pouze jeden datový prvek. Například jedno celé číslo, číslo s plovoucí desetinnou čárkou nebo prvek pole. Některé novější procesory mají větší Registry označované jako vektorové Registry, které mohou obsahovat malé pole dat. Vzhledem k tomu, že jsou ve velkém množství dat, vektorové Registry umožňují provádět operace zahrnující pole velmi rychle. Vektorové Registry se nejdřív používaly u drahých, vysoce výkonných počítačů, ale teď jsou dostupné na mikroprocesorech, kde se používají k Skvělé výhodě náročných grafických operací.

 Procesor má obvykle dvě sady registrů pro obecné účely, jedno optimalizované pro operace s plovoucí desetinnou čárkou a druhý pro celočíselné operace. Nepřekvapivě se nazývají s plovoucí desetinnou čárkou a celočíselnými Registry.

 Spravovaný kód je kompilován v době běhu do nativního kódu, který přistupuje k fyzickým registrům mikroprocesoru. Okno **Registry** zobrazí tyto fyzické registry pro modul CLR (Common Language Runtime) nebo nativní kód. Okno **Registry** nezobrazuje informace o registraci pro skript nebo aplikaci SQL, protože skript a SQL jsou jazyky, které nepodporují koncept registrů.

 Další informace o zobrazení okna **Registry** naleznete v tématu [using the Registry Window](../debugger/how-to-use-the-registers-window.md).

 Když se podíváte na okno **Registry** , zobrazí se položky, například `EAX = 003110D8`.

 Symbol nalevo od znaménka `=` je název registru, `EAX` v tomto případě. Číslo napravo od znaménka `=` představuje obsah registru.

 Okno **Registry** umožňuje provádět více než jenom zobrazení obsahu registru. Pokud jste v režimu pozastavení v nativním kódu, můžete kliknout na obsah registru a upravit hodnotu. To není něco, co byste měli dělat náhodně. Pokud nerozumíte upravovanému registru a data, která obsahuje, výsledkem úprav nepozorný je pravděpodobně chyba programu nebo jiná Nepožadovaná důsledek. Podrobnější vysvětlení registračních sad různých procesorů Intel a Intel, které jsou nad rámec tohoto stručného úvodu, je mnohem vyšší.

## <a name="register-groups"></a>Registrovat skupiny

Chcete-li snížit přehlednost, okno **Registry** uspořádá Registry do skupin. Pokud kliknete pravým tlačítkem myši na okno **Registry** , zobrazí se místní nabídka obsahující seznam skupin, které můžete zobrazit nebo skrýt podle potřeby.

## <a name="register-flags"></a>Příznaky registru

Pro procesory Intel x86 se můžou v okně **Registry** zobrazit následující příznaky. Během relace ladění můžete tyto příznaky také upravit.

|příznaků|Nastavit hodnotu|
|-|-|
|Plně|OV = 1|
|Směr|NAHORU = 1|
|Jakkoli|EI = 1|
|Osobě|PL = 1|
|Nula|ZR = 1|
|Pomocná pomocná|AC = 1|
|Parita|PE = 1|
|Úmysl|CY = 1|

## <a name="see-also"></a>Viz také:
- [Postupy: Použití okna Registry](../debugger/how-to-use-the-registers-window.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)