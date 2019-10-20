---
title: Proces transformace textové šablony | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7322724b2118cb8b844262696a6e7cbd91a74e9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658496"
---
# <a name="the-text-template-transformation-process"></a>Proces transformace textových šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces transformace textové šablony převede soubor textové šablony jako vstup a vygeneruje nový textový soubor jako výstup. Můžete například použít šablony textu k vygenerování Visual Basic nebo C# kódu nebo můžete vygenerovat sestavu HTML.

 Tyto tři komponenty se účastní tohoto procesu: modul, hostitel a procesory direktiv. Modul řídí proces; komunikuje s hostitelem a procesorem direktiv, aby vytvořil výstupní soubor. Hostitel poskytuje jakoukoli interakci s prostředím, jako je například vyhledání souborů a sestavení. Procesor direktiv přidává funkce, jako je například čtení dat ze souboru XML nebo databáze.

 Proces transformace textové šablony se provádí ve dvou krocích. Za prvé vytvoří modul dočasnou třídu, která je známá jako vygenerovaná transformační třída. Tato třída obsahuje kód, který je generován direktivami a řídicími bloky. Poté modul zkompiluje a spustí generovanou třídu transformace pro vytvoření výstupního souboru.

## <a name="components"></a>Komponenty

|Součást|Popis|Přizpůsobitelné (ano/ne)|
|---------------|-----------------|------------------------------|
|Jádra|Komponenta Engine řídí proces transformace textové šablony.|Ne.|
|Hostitel|Hostitel je rozhraní mezi modulem a uživatelským prostředím. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je hostitelem procesu transformace textu.|Ano. Můžete napsat vlastního hostitele.|
|Procesory direktiv|Procesory direktiv jsou třídy, které zpracovávají direktivy v textových šablonách. Direktivy můžete použít k poskytnutí dat pro textovou šablonu ze vstupního zdroje.|Ano. Můžete psát vlastní procesory direktiv.|

## <a name="the-engine"></a>Modul
 Modul obdrží šablonu jako řetězec z hostitele, který zpracovává všechny soubory, které jsou používány v procesu transformace. Modul pak vyzve hostitele k vyhledání jakýchkoli vlastních procesorů směrnice a dalších aspektů prostředí. Modul pak zkompiluje a spustí generovanou transformační třídu. Modul vrátí vygenerovaný text na hostitele, který obvykle ukládá text do souboru.

## <a name="the-host"></a>Hostitel
 Hostitel zodpovídá za cokoli, co souvisí s prostředím mimo proces transformace, včetně následujících:

- Hledání textu a binárních souborů požadovaných modulem nebo procesorem direktiv. Hostitel může vyhledat sestavení v adresářích a v globální mezipaměti sestavení (GAC). Hostitel může vyhledat vlastní kód procesoru direktiv pro modul. Hostitel může také vyhledat a číst textové soubory a vracet jejich obsah jako řetězce.

- Poskytování seznamů standardních sestavení a oborů názvů, které modul používá k vytvoření vygenerované třídy transformace.

- Poskytnutí domény aplikace, která se používá, když modul zkompiluje a spustí generovanou třídu transformace. K ochraně hostitelské aplikace před chybami v kódu šablony se používá samostatná aplikační doména.

- Zápis vygenerovaného výstupního souboru.

- Nastavení výchozí přípony pro vygenerovaný výstupní soubor.

- Zpracování chyb transformace šablony textu. Například hostitel může zobrazit chyby v uživatelském rozhraní nebo je zapsat do souboru. (V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se chyby zobrazují v okně chybová zpráva.)

- Poskytnutí požadované hodnoty parametru, pokud uživatel volal direktivu bez zadání hodnoty. Procesor direktiv může zadat název direktivy a parametr a požádat hostitele, aby poskytl výchozí hodnotu, pokud má jednu z nich.

## <a name="directives-and-directive-processors"></a>Procesory direktiv a direktiv
 Direktiva je příkaz v textové šabloně. Poskytuje parametry procesu generování. Obvykle direktivy definují zdroj a typ modelu nebo jiného vstupu a příponu názvu výstupního souboru.

 Procesor direktiv může zpracovat jednu nebo více direktiv. Při transformaci šablony je nutné nainstalovat procesor direktiv, který se může zabývat direktivami ve vaší šabloně.

 Direktivy fungují přidáním kódu do vygenerované třídy transformace. Direktivy voláte z textové šablony a modul zpracovává všechna volání direktiv při vytváření vygenerované třídy transformace. Po úspěšném volání direktivy může zbytek kódu, který píšete v textové šabloně, spoléhat na funkčnost, kterou poskytuje tato direktiva. Například můžete provést následující volání direktivy `import` v šabloně:

 `<#@ import namespace="System.Text" #>`

 Procesor standardní směrnice převede tento údaj na příkaz `using` ve vygenerované třídě transformace. Pak můžete použít třídu `StringBuilder` ve zbytku kódu šablony bez toho, aby byla kvalifikována jako `System.Text.StringBuilder`.
