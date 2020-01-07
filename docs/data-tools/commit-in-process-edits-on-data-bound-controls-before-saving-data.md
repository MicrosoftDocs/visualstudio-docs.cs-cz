---
title: Potvrzení úprav v procesu v ovládacích prvcích vázaných na data před uložením
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4a708128f827568e072c617effff17129e41e558
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586936"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Potvrzení úprav v procesu v ovládacích prvcích vázaných na data před uložením dat

Při úpravách hodnot v ovládacích prvcích vázaných na data musí uživatelé přejít na aktuální záznam a potvrdit aktualizovanou hodnotu do podkladového zdroje dat, ke kterému je ovládací prvek vázán. Když přetáhnete položky z [okna zdroje dat](add-new-data-sources.md) do formuláře, první položka, kterou jste vyřadíte, vygeneruje kód do události kliknutí na tlačítko pro **uložení** <xref:System.Windows.Forms.BindingNavigator>. Tento kód volá metodu <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource>. Proto se volání metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> generuje pouze pro první <xref:System.Windows.Forms.BindingSource>, která je přidána do formuláře.

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> volá potvrzení změn, které jsou v procesu, v jakémkoli ovládacím prvku vázaném na data, který je právě upravován. Proto pokud ovládací prvek vázaný na data stále obsahuje fokus a kliknete na tlačítko **Uložit** , všechny čekající úpravy v tomto ovládacím prvku se potvrdí před samotným uložením (`TableAdapterManager.UpdateAll` metoda).

Aplikaci můžete nakonfigurovat tak, aby automaticky provedla změny, a to i v případě, že se uživatel pokusí uložit data bez potvrzení změn, a to v rámci procesu ukládání.

> [!NOTE]
> Návrhář přidá kód `BindingSource.EndEdit` pouze pro první položku vyhozenou na formuláři. Proto je nutné přidat řádek kódu pro volání metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> pro každý <xref:System.Windows.Forms.BindingSource> na formuláři. Můžete ručně přidat řádek kódu pro volání metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> pro každý <xref:System.Windows.Forms.BindingSource>. Alternativně můžete do formuláře přidat metodu `EndEditOnAllBindingSources` a před provedením uložení ji volat.

Následující kód používá dotaz [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) k iteraci všech <xref:System.Windows.Forms.BindingSource> komponent a volání metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> pro každý <xref:System.Windows.Forms.BindingSource> na formuláři.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Volání metodu EndEdit volat pro všechny komponenty BindingSource na formuláři

1. Do formuláře obsahujícího komponenty <xref:System.Windows.Forms.BindingSource> přidejte následující kód.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Přidejte následující řádek kódu těsně před všechna volání k uložení dat formuláře (metoda `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
