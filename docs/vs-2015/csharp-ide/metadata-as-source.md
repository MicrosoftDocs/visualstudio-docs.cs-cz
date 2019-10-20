---
title: Metadata jako zdroj | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b1d96224be13a12dcaadb394584f8441c7bd1934
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667513"
---
# <a name="metadata-as-source"></a>Metadata jako zdroj
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metadata as source umožňují zobrazit metadata, která se zobrazí jako C# zdrojový kód ve vyrovnávací paměti jen pro čtení. To umožňuje zobrazit deklarace typů a členů (bez implementace). Metadata můžete zobrazit jako zdroj spuštěním příkazu **Přejít k definici** pro typy nebo členy, jejichž zdrojový kód není dostupný z vašeho projektu nebo řešení.

> [!NOTE]
> Při pokusu o spuštění příkazu **Přejít k definici** pro typy nebo členy, které jsou označeny jako interní, integrované vývojové prostředí (IDE) nezobrazuje své metadata jako zdroj, bez ohledu na to, zda odkazující sestavení je přítel nebo ne.

 Metadata můžete zobrazit jako zdroj v editoru kódu nebo v okně **definice kódu** .

## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Zobrazení metadat jako zdroje v editoru kódu
 Když spustíte příkaz **Přejít na definici** pro položku, jejíž zdrojový kód není k dispozici, dokument s kartami, který obsahuje zobrazení metadat této položky, zobrazených jako zdroj, se zobrazí v editoru kódu. Název typu, za nímž následuje **[from metadata]** , se zobrazí na kartě dokumentu.

 Například pokud spustíte příkaz **Přejít na definici** pro <xref:System.Console>, metadata pro <xref:System.Console> se zobrazí v editoru kódu jako C# zdrojový kód, který se podobá deklaraci, ale bez implementace.

 ![Metadata jako zdroj](../csharp-ide/media/metadatasource.png "MetadataSource")

## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Zobrazení metadat jako zdroje v okně Definice kódu
 Když je okno **definice kódu** aktivní nebo viditelné, IDE automaticky spustí příkaz **Přejít k definici** pro položky pod kurzorem v editoru kódu a pro položky, které jsou vybrány v **zobrazení tříd** nebo **Prohlížeč objektů**. Pokud není zdrojový kód pro tuto položku k dispozici, rozhraní IDE zobrazí metadata položky jako zdroj v okně **definice kódu** .

 Například pokud umístíte kurzor do slova <xref:System.Console> v editoru kódu, metadata pro <xref:System.Console> v okně **definice kódu** se zobrazí jako zdroj. Zdroj se podobá deklaraci <xref:System.Console>, ale bez implementace.

 Pokud chcete zobrazit deklaraci položky, která se zobrazí v okně **definice kódu** , klikněte pravým tlačítkem myši na položku a klikněte na **Přejít k definici**.