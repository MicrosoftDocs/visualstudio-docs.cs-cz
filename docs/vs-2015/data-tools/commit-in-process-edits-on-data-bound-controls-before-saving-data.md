---
title: Potvrzení úprav v procesu v ovládacích prvcích vázaných na data před uložením dat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662453"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Potvrzení úprav v procesu v ovládacích prvcích vázaných na data před uložením dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při úpravách hodnot v ovládacích prvcích vázaných na data musí uživatelé přejít na aktuální záznam a potvrdit aktualizovanou hodnotu do podkladového zdroje dat, ke kterému je ovládací prvek vázán. Když přetáhnete položky z [okna zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do formuláře, první položka, kterou jste vyřadíte, vygeneruje kód do události kliknutí na tlačítko pro **uložení** <xref:System.Windows.Forms.BindingNavigator>. Tento kód volá metodu <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource>. Proto se volání metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> generuje pouze pro první <xref:System.Windows.Forms.BindingSource>, která je přidána do formuláře.

 @No__t_0 volá potvrzení změn, které jsou v procesu, v jakémkoli ovládacím prvku vázaném na data, který je právě upravován. Proto pokud ovládací prvek vázaný na data stále obsahuje fokus a kliknete na tlačítko **Uložit** , všechny čekající úpravy v tomto ovládacím prvku se potvrdí před samotným uložením (`TableAdapterManager.UpdateAll` metoda).

 Aplikaci můžete nakonfigurovat tak, aby automaticky provedla změny, a to i v případě, že se uživatel pokusí uložit data bez potvrzení změn, a to v rámci procesu ukládání.

> [!NOTE]
> Návrhář přidá kód `BindingSource.EndEdit` pouze pro první položku vyhozenou na formuláři. Proto je nutné přidat řádek kódu pro volání metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> pro každý <xref:System.Windows.Forms.BindingSource> na formuláři. Můžete ručně přidat řádek kódu pro volání metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> pro každý <xref:System.Windows.Forms.BindingSource>. Alternativně můžete do formuláře přidat metodu `EndEditOnAllBindingSources` a před provedením uložení ji volat.

 Následující kód používá dotaz [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) k iteraci všech <xref:System.Windows.Forms.BindingSource> komponent a volání metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> pro každý <xref:System.Windows.Forms.BindingSource> na formuláři.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Volání metodu EndEdit volat pro všechny komponenty BindingSource na formuláři

1. Do formuláře obsahujícího komponenty <xref:System.Windows.Forms.BindingSource> přidejte následující kód.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Přidejte následující řádek kódu těsně před všechna volání k uložení dat formuláře (metoda `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>Viz také
 [Vázání ovládacích prvků model Windows Forms k datům v](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [hierarchické aktualizaci](../data-tools/hierarchical-update.md) sady Visual Studio
