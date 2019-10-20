---
title: 'Ukázka rozšíření aplikace Excel: třída ExtensionPackage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1c1f4c746fa505b50bab9caa7a516a2abc77f69
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672201"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Ukázka rozšíření aplikace Excel: třída ExtensionPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato třída rozšiřuje třídu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> a poskytuje vstupní bod pro programový test UI, který testuje [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] list.

## <a name="assembly-attribute"></a>Atribut Assembly
 Soubor začíná atributem sestavení, který identifikuje sestavení jako rozšíření testu uživatelského rozhraní.

```
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
    "ExcelExtensionPackage",
    typeof(
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]
```

 Tento atribut deklaruje název základní třídy, název třídy balíčku a plně kvalifikovaný název třídy pro vlastní třídu balíčku rozšíření.

## <a name="simple-properties"></a>Jednoduché vlastnosti
 Tato třída obsahuje vlastnosti, které poskytují hodnoty, které jsou používány rozhraním programového testování uživatelského rozhraní k identifikaci a popisu rozšíření a sestavení. Další informace najdete v komentářích ke kódu.

## <a name="getservice-method"></a>GetService – Metoda
 Metoda <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> je jedním vstupním bodem, který je používán rozhraním programového testování uživatelského rozhraní, k získání přístupu k poskytovateli technologie, zprostředkovateli vlastností a filtru akcí, jak je identifikovaný základní třídou pro každý objekt.

## <a name="see-also"></a>Viz také
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> [Rozšiřování programových testů uživatelského rozhraní a záznamů akcí pro podporu aplikace Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
