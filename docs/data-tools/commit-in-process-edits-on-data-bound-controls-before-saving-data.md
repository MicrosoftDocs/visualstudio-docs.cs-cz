---
title: Nepotvrzené úpravy
description: Před uložením dat potvrďte změny v procesu model Windows Forms ovládacích prvků vázaných na data. Pro všechny komponenty BindingSource na formuláři volejte metodu EndEdit volat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 53101505230a51f109ace904c2f8322659733b4b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216316"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Potvrzení úprav v procesu v ovládacích prvcích vázaných na data před uložením dat

Při úpravách hodnot v ovládacích prvcích vázaných na data musí uživatelé přejít na aktuální záznam a potvrdit aktualizovanou hodnotu do podkladového zdroje dat, ke kterému je ovládací prvek vázán. Když přetáhnete položky z [okna zdroje dat](add-new-data-sources.md) do formuláře, první položka, kterou jste vyřadíte, vygeneruje kód do události kliknutí na tlačítko **Uložit** <xref:System.Windows.Forms.BindingNavigator> . Tento kód volá <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodu <xref:System.Windows.Forms.BindingSource> . Proto volání <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody je vygenerováno pouze pro první <xref:System.Windows.Forms.BindingSource> , která je přidána do formuláře.

<xref:System.Windows.Forms.BindingSource.EndEdit%2A>Volání potvrdí všechny probíhající změny v rámci všech ovládacích prvků vázaných na data, které jsou právě upravovány. Proto pokud ovládací prvek vázaný na data stále obsahuje fokus a kliknete na tlačítko **Uložit** , všechny čekající úpravy v tomto ovládacím prvku budou potvrzeny před samotným uložením ( `TableAdapterManager.UpdateAll` Metoda).

Aplikaci můžete nakonfigurovat tak, aby automaticky provedla změny, a to i v případě, že se uživatel pokusí uložit data bez potvrzení změn, a to v rámci procesu ukládání.

> [!NOTE]
> Návrhář přidá `BindingSource.EndEdit` kód pouze pro první položku zrušenou na formuláři. Proto je nutné přidat řádek kódu pro volání <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody pro každý <xref:System.Windows.Forms.BindingSource> formulář. Můžete ručně přidat řádek kódu pro volání <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody pro každý <xref:System.Windows.Forms.BindingSource> . Alternativně můžete přidat `EndEditOnAllBindingSources` metodu do formuláře a volat ji před provedením uložení.

Následující kód používá dotaz [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) k iterování všech <xref:System.Windows.Forms.BindingSource> komponent a volání <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody pro každý <xref:System.Windows.Forms.BindingSource> formulář.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Volání metodu EndEdit volat pro všechny komponenty BindingSource na formuláři

1. Do formuláře, který obsahuje komponenty, přidejte následující kód <xref:System.Windows.Forms.BindingSource> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Přidejte následující řádek kódu těsně před jakékoli volání k uložení dat formuláře ( `TableAdapterManager.UpdateAll()` Metoda):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
