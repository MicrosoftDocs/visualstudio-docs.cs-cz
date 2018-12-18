---
title: Proces transformace textových šablon
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1ace7528eb1685765fe5c7ff11ce9b3c3234a941
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919153"
---
# <a name="the-text-template-transformation-process"></a>Proces transformace textových šablon
Proces transformace textových šablon přijímá jako vstupní soubor textové šablony a vygeneruje nový textový soubor jako výstup. Například textové šablony můžete použít ke generování kódu jazyka Visual Basic nebo C#, nebo můžete vygenerovat zprávu ve formátu HTML.

 Tři komponenty účasti v tomto procesu: modul, hostitele a procesory direktiv. Modul řídí procesu. komunikuje se službou hostitele a procesor direktiv pro vytvoření výstupního souboru. Hostitel poskytuje všechny interakce s prostředím, jako je hledání souborů a sestavení. Procesor direktiv přidá funkce, jako je například čtení dat ze souboru XML nebo databáze.

 Proces transformace textových šablon se provádí ve dvou krocích. Modul nejprve vytvoří dočasnou třídu, která se nazývá vygenerované třídy transformace. Tato třída obsahuje kód, který je generován direktivy a řídicí bloky. Potom modul zkompiluje a spustí vygenerované třídy transformace pro vytvoření výstupního souboru.

## <a name="components"></a>Součásti

|Součást|Popis|Přizpůsobitelné (Ano/Ne)|
|-|-|-|
|Modul|Komponenta modulu řídí proces transformace textových šablon|Ne.|
|Hostitel|Hostitel je rozhraní mezi modul a uživatelského prostředí. Visual Studio je hostitel procesu transformace textu.|Ano. Můžete vytvořit vlastního hostitele.|
|Procesory direktiv|Procesory direktiv jsou třídy, které zpracovávají direktivy v textových šablonách. Můžete použít direktivy předávat data do textové šablony ze vstupního zdroje.|Ano. Můžete napsat vlastní procesory direktiv|

## <a name="the-engine"></a>Modul
 Modul přijímá jako řetězec z hostitele, která zpracovává všechny soubory, které se používají v transformace procesu šablony. Modul následně požádá hostitele najít všechny vlastní procesory direktiv a další aspekty životního prostředí. Modul se potom zkompiluje a spustí vygenerované třídy transformace. Modul vrátí generovaný text na hostitele, který obvykle uloží text do souboru.

## <a name="the-host"></a>Hostitel
 Hostitel je zodpovědná za nic, které se týkají prostředí mimo proces transformace, včetně následujících:

-   Hledání textu a binárních souborů požadoval modul nebo procesor direktiv. Hostitel může prohledáním adresáře a globální mezipaměti sestavení k vyhledání sestavení. Hostitele můžete vyhledat kód vlastního procesoru direktiv pro tento motor. Hostitel můžete také najít a čtení textových souborů a vrátí jejich obsah jako řetězce.

-   Poskytuje seznam standardní sestavení a obory názvů, které se používají modulem vytvořit vygenerované třídy transformace.

-   Poskytování doménu aplikace, který se používá, když modul zkompiluje a spustí vygenerované třídy transformace. Pokud chcete ochránit před chybami v kódu šablony hostitele aplikace se používá zvláštní aplikační doména.

-   Zápis vygenerovaného výstupního souboru.

-   Nastavení výchozí přípona pro generovaný soubor.

-   Zpracování chyb transformace textové šablony. Hostitele můžete například zobrazit chyby v uživatelském rozhraní nebo zápis do souboru. (V sadě Visual Studio se zobrazí chyby v okně chybové zprávy.)

-   Poskytuje hodnotu požadovaného parametru, pokud uživatel má direktivu volána bez zadání hodnoty. Procesoru direktiv můžete zadat název směrnice a parametr a požádejte hostitele tak, aby zadat výchozí hodnotu, pokud jej obsahuje.

## <a name="directives-and-directive-processors"></a>Direktivy a procesorů pro direktivy
 Direktivy je příkaz v textové šabloně. Poskytuje parametry pro proces generování. Obvykle direktivy definovat zdroje a typ modelu nebo ostatní vstupy a příponu názvu souboru výstupního souboru.

 Procesor direktiv může zpracovat jeden nebo více direktiv. Při transformaci šablony, je třeba mít nainstalovanou procesor direktiv, který můžete řešit pomocí direktivy v šabloně.

 Direktivy fungovat tak, že přidáte kód do vygenerované třídy transformace. Direktivy textové šablony a procesy modulu direktiv volání volání vytvoří vygenerované třídy transformace. Po úspěšně zavolat direktivu zbytek kódu, který napíšete do textové šablony se můžete spolehnout na funkce, které poskytuje tato direktiva. Například můžete provést následující volání `import` direktiv v šabloně:

 `<#@ import namespace="System.Text" #>`

 Převede standardní procesoru direktiv pro `using` prohlášení do vygenerované třídy transformace. Pak můžete použít `StringBuilder` třídy ve zbytku kódu bez kvalifikace ho jako šablonu `System.Text.StringBuilder`.