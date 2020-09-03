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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660425"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Ukázka rozšíření aplikace Excel: třída PropertyProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato interní třída rozšiřuje <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> třídu a poskytuje služby vlastností pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] prvky pro záznam a přehrávání testů uživatelského rozhraní (UI).

## <a name="getcontrolsupportlevel-method"></a>Metoda GetControlSupportLevel
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A>Metoda vrátí číslo, které označuje úroveň podpory, kterou může zprostředkovatel vlastností nabídnout pro poskytnutý ovládací prvek. Čím vyšší je vrácená hodnota, tím více zprostředkovatel vlastností může ovládací prvek podporovat. V tomto případě metoda kontroluje hodnotu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> vlastnosti poskytnutého ovládacího prvku. Pokud je hodnota "Excel" a je-li <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> uvedeno, že se jedná o `CellElement` , vrátí metoda nejvyšší hodnotu. v opačném případě vrátí hodnotu nula, což znamená, že není poskytnuta žádná podpora.

## <a name="getpropertynames-method"></a>Getpropertynames – metoda
 Vrátí slovník názvů vlastností a popisovačů vlastností pro podporované vlastnosti ovládacího prvku buňky aplikace Excel.

## <a name="getpropertydescriptor-method"></a>Metoda GetPropertyDescriptor
 Tato metoda je volána rozhraním testování, aby získala předdefinované deskriptor vlastnosti pro poskytnutý název vlastnosti.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Metody GetPropertyValue a SetPropertyValue
 `GetPropertyValue`Metoda používá `Communicator` třídu tohoto rozšíření k vrácení hodnoty vlastnosti z Excelu. `SetPropertyValue`Metoda používá <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> třídu a `Communicator` komponentu k nastavení hodnoty vlastnosti. Tyto metody jsou volány testovacím rozhraním.

## <a name="code-generation-customization-methods"></a>Metody přizpůsobení generování kódu
 Tyto metody nejsou pro toto rozšíření implementovány. Proto buď vrátí, `null` nebo vyvolají <xref:System.NotImplementedException> .

## <a name="see-also"></a>Viz také
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
 [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
