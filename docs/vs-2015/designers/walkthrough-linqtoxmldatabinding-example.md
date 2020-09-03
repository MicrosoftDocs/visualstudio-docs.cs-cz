---
title: 'Návod: příklad příkladu LinqToXmlDataBinding | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e97d612e19f64110f3090029dcff82acbad8e87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663974"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Návod: Příklad LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod popisuje příklad příkladu LinqToXmlDataBinding a vysvětluje některé zajímavé obsahy svých dvou primárních zdrojových souborů, zdrojový kód L2DBForm. XAML a L2DBForm.xaml.cs.

## <a name="prerequisites"></a>Požadavky
 Než si přečtete tento návod, důrazně doporučujeme sestavit a spustit program příkladu LinqToXmlDataBinding, jak je popsáno v tématu [Postupy: sestavení a spuštění příkladu LinqToXmlDataBinding příkladu](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).

## <a name="remarks"></a>Poznámky
 Program příkladu LinqToXmlDataBinding je aplikace Windows Presentation Foundation (WPF), která se skládá ze zdrojových souborů C# a XAML. Obsahuje vložený dokument XML, který definuje seznam knih a umožňuje uživateli zobrazovat, přidávat, odstraňovat a upravovat tyto položky. Skládá se z následujících dvou primárních zdrojových souborů:

- Zdrojový kód L2DBForm. XAML obsahuje kód deklarace XAML pro uživatelské rozhraní (UI) hlavního okna. Obsahuje také oddíl prostředků okna definující poskytovatele dat a vložený dokument XML pro výpisy knih.

- L2DBForm.xaml.cs obsahuje metody inicializace a zpracování událostí přidružené k uživatelskému rozhraní.

  Hlavní okno je rozdělené do následujících čtyř oddílů vertikálního uživatelského rozhraní:

- **XML** zobrazí nezpracovaný zdroj XML se seznamem vložených knih.

- **Seznam knih** zobrazuje položky knihy jako standardní text a umožňuje uživateli vybrat a odstranit jednotlivé položky.

- **Možnost upravit vybranou knihu** umožňuje uživateli upravovat hodnoty spojené s aktuálně vybranou položkou knihy.

- Možnost **Přidat novou knihu** umožňuje vytvořit novou položku knihy na základě hodnot zadaných uživatelem.

## <a name="in-this-section"></a>V tomto oddílu

|Téma|Popis|
|-----------|-----------------|
|[Zdrojový kód zdrojový kód L2DBForm. XAML](../designers/l2dbform-xaml-source-code.md)|Obsahuje obsah a popis kódu XAML v souboru zdrojový kód L2DBForm. XAML.|
|[Zdrojový kód L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Obsahuje obsah a popis zdrojového kódu jazyka C# v souboru L2DBForm.xaml.cs.|

## <a name="see-also"></a>Viz také
 [Datová vazba WPF pomocí LINQ to XML příklad](../designers/wpf-data-binding-using-linq-to-xml-example.md) [: sestavení a spuštění příkladu příkladu LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)
