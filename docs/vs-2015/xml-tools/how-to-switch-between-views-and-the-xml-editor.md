---
title: 'Postupy: přepínání mezi zobrazeními a editorem XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28267f705dd9a747d0e3f3ac5dc2869ab7de8f6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656322"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Postupy: přepínání mezi zobrazeními a editorem XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma ukazuje, jak přepínat mezi zobrazeními v Návrháři schématu XML (Návrhář XSD) a editorem XML. V tomto příkladu se používá [schéma nákupních objednávek](../xml-tools/sample-xsd-file-simple-schema.md).

### <a name="to-switch-between-the-views-and-the-xml-editor"></a>Přepínání mezi zobrazeními a editorem XML

1. Chcete-li vytvořit a upravit nový soubor schématu XML, postupujte podle kroků v tématu [Postupy: vytvoření a úprava souboru schématu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Chcete-li přepnout do návrháře schématu XML z editoru XML, klikněte pravým tlačítkem myši kdekoli v editoru XML a vyberte možnost **Návrhář zobrazení**.

3. Chcete-li přepnout na zobrazení grafu pomocí meze, klikněte na tlačítko **použít zobrazení grafu, abyste viděli vztah mezi uzly** v zobrazení Start.

4. Přetáhněte uzel `USAddress` z Průzkumníka schémat XML do zobrazení grafu. V zobrazení grafu klikněte pravým tlačítkem myši na uzel `USAddress` a v místní nabídce vyberte možnost **Zobrazit v zobrazení modelu obsahu** .

     Zobrazí se zobrazení model obsahu se zobrazenými podrobnostmi uzlu `USAddress`.

5. Chcete-li přepnout do zobrazení začátek ze zobrazení modelu obsahu pomocí panelu nástrojů, klikněte na tlačítko Spustit zobrazení na panelu nástrojů XSD.

6. Chcete-li přepínat mezi zobrazeními pomocí klávesových zkratek, stiskněte klávesy CTRL + 1 pro zobrazení Start, CTRL + 2 pro zobrazení grafu a kombinaci kláves CTRL + 3 pro zobrazení modelu obsahu.

7. Chcete-li přejít do editoru XML ze zobrazení modelu obsahu, klikněte pravým tlačítkem myši na uzel a v místní nabídce vyberte možnost **Zobrazit kód** .
