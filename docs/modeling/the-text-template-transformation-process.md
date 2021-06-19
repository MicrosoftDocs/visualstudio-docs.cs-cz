---
title: Proces transformace textových šablon
description: Zjistěte, že proces transformace textové šablony přebírá jako vstup textový soubor šablony a jako výstup vygeneruje nový textový soubor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dc827039253c21effffcc82d70b4f66ff284738
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388591"
---
# <a name="the-text-template-transformation-process"></a>Proces transformace textových šablon
Proces transformace textové šablony převezme jako vstup textový soubor šablony a jako výstup vygeneruje nový textový soubor. Můžete například použít textové šablony ke generování kódu Visual Basic nebo C#, nebo můžete vygenerovat sestavu HTML.

 Součástí tohoto procesu jsou tři komponenty: modul, hostitel a procesory direktiv. Proces řídí modul. Komunikuje s hostitelem a procesorem direktiv a vytváří výstupní soubor. Hostitel poskytuje jakoukoli interakci s prostředím, například vyhledání souborů a sestavení. Procesor direktiv přidává funkce, například čtení dat ze souboru XML nebo databáze.

 Proces transformace textové šablony se provádí ve dvou krocích. Nejprve modul vytvoří dočasnou třídu, která se označuje jako vygenerovaná třída transformace. Tato třída obsahuje kód, který je generován direktivy a řídicími bloky. Potom modul zkompiluje a spustí vygenerovanou třídu transformace pro vytvoření výstupního souboru.

## <a name="components"></a>Komponenty

|Komponenta|Popis|Přizpůsobitelné (Ano/Ne)|
|-|-|-|
|Modul|Komponenta modulu řídí proces transformace textové šablony.|No.|
|Hostitel|Hostitel je rozhraní mezi strojem a uživatelským prostředím. Visual Studio je hostitelem procesu transformace textu.|Ano. Můžete napsat vlastního hostitele.|
|Procesory direktiv|Procesory direktiv jsou třídy, které zpracování direktiv v textových šablonách. Direktivy můžete použít k poskytnutí dat do textové šablony ze vstupního zdroje.|Ano. Můžete psát vlastní procesory direktiv.|

## <a name="the-engine"></a>Modul
 Modul obdrží šablonu jako řetězec od hostitele, který zpracovává všechny soubory, které se používají v procesu transformace. Modul pak požádá hostitele o vyhledání vlastních procesorů direktiv a dalších aspektů prostředí. Modul pak zkompiluje a spustí vygenerovanou transformační třídu. Modul vrátí vygenerovaný text hostiteli, který obvykle ukládá text do souboru.

## <a name="the-host"></a>Hostitel
 Hostitel zodpovídá za všechno, co souvisí s prostředím mimo proces transformace, včetně následujících:

- Vyhledání textových a binárních souborů požadovaných strojem nebo procesorem direktiv Hostitel může prohledávat adresáře a globální mezipaměť sestavení (GAC) pro vyhledání sestavení. Hostitel může vyhledat vlastní kód procesoru direktiv pro modul. Hostitel může také vyhledat a číst textové soubory a vracet jejich obsah jako řetězce.

- Poskytuje seznamy standardních sestavení a oborů názvů, které modul používá k vytvoření vygenerované třídy transformace.

- Poskytnutí domény aplikace, která se používá, když se modul zkompiluje a spustí vygenerovanou transformační třídu. K ochraně hostitelské aplikace před chybami v kódu šablony se používá samostatná doména aplikace.

- Zápis vygenerovaný výstupní soubor.

- Nastavení výchozí přípony pro vygenerovaný výstupní soubor

- Zpracování chyb transformace textových šablon Hostitel může například zobrazit chyby v uživatelském rozhraní nebo je zapsat do souboru. (V Visual Studio se chyby zobrazují v okně chybové zprávy.)

- Poskytnutí požadované hodnoty parametru, pokud uživatel volal direktivu bez zadání hodnoty. Procesor direktiv může zadat název direktivy a parametr a požádat hostitele o zadání výchozí hodnoty, pokud ji má.

## <a name="directives-and-directive-processors"></a>Direktivy a procesory direktiv
 Direktiva je příkaz v textové šabloně. Poskytuje parametry procesu generování. Direktivy obvykle definují zdroj a typ modelu nebo jiného vstupu a příponu názvu souboru výstupního souboru.

 Procesor direktiv může zpracovat jednu nebo více direktiv. Při transformaci šablony musíte mít nainstalovaný procesor direktiv, který dokáže direktivy v šabloně řešit.

 Direktivy fungují tak, že přidávají kód do vygenerované třídy transformace. Direktivy voláte z textové šablony a modul zpracovává všechna volání direktiv při vytváření vygenerované třídy transformace. Po úspěšném volání direktivy se zbytek kódu, který napíšete v textové šabloně, může spoléhat na funkce poskytované direktivou . Můžete například provést následující volání `import` direktivy v šabloně:

 `<#@ import namespace="System.Text" #>`

 Standardní procesor direktiv převede tuto hodnotu na `using` příkaz ve vygenerované transformační třídě. Pak můžete použít třídu ve zbytku kódu šablony, aniž `StringBuilder` byste ji kvalifikují jako `System.Text.StringBuilder` .
