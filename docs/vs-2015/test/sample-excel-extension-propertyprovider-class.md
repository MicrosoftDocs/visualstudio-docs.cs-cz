---
title: 'Ukázka rozšíření aplikace Excel: třída PropertyProvider | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ae254f85b00c47ba00250641f7afe0a638ceabc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660425"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Ukázka rozšíření aplikace Excel: třída PropertyProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato interní třída rozšiřuje třídu <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> a poskytuje služby vlastností pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] prvky pro záznam a přehrávání testů uživatelského rozhraní (UI).

## <a name="getcontrolsupportlevel-method"></a>Metoda GetControlSupportLevel
 Metoda <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> vrátí číslo, které označuje úroveň podpory, kterou může zprostředkovatel vlastností nabídnout pro poskytnutý ovládací prvek. Čím vyšší je vrácená hodnota, tím více zprostředkovatel vlastností může ovládací prvek podporovat. V tomto případě metoda kontroluje hodnotu vlastnosti <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> poskytnutého ovládacího prvku. Pokud je hodnota "Excel" a pokud <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> označuje, že se jedná o `CellElement`, vrátí tato metoda nejvyšší hodnotu; v opačném případě vrátí hodnotu nula, což znamená, že žádná podpora není k dispozici.

## <a name="getpropertynames-method"></a>Getpropertynames – metoda
 Vrátí slovník názvů vlastností a popisovačů vlastností pro podporované vlastnosti ovládacího prvku buňky aplikace Excel.

## <a name="getpropertydescriptor-method"></a>Metoda GetPropertyDescriptor
 Tato metoda je volána rozhraním testování, aby získala předdefinované deskriptor vlastnosti pro poskytnutý název vlastnosti.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Metody GetPropertyValue a SetPropertyValue
 Metoda `GetPropertyValue` používá třídu `Communicator` tohoto rozšíření k vrácení hodnoty vlastnosti z Excelu. Metoda `SetPropertyValue` používá třídu <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> a komponentu `Communicator` k nastavení hodnoty vlastnosti. Tyto metody jsou volány testovacím rozhraním.

## <a name="code-generation-customization-methods"></a>Metody přizpůsobení generování kódu
 Tyto metody nejsou pro toto rozšíření implementovány. Proto buď vrátí `null` nebo vyvolejte <xref:System.NotImplementedException>.

## <a name="see-also"></a>Viz také
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider><xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
 [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
