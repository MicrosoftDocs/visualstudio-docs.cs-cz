---
title: Návrhář aktivity TryCatch | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 74b54ef6b82e4f98ab94972b5d9b0155c16060a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240991"
---
# <a name="trycatch-activity-designer"></a>Návrhář aktivity TryCatch
**TryCatch** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.TryCatch> aktivity.  
  
## <a name="the-trycatch-activity"></a>Aktivita TryCatch  
 <xref:System.Activities.Statements.TryCatch> Obsahuje aktivity <xref:System.Activities.Statements.TryCatch.Try%2A> aktivity, kolekce **Catch\<TException >** a <xref:System.Activities.Statements.TryCatch.Finally%2A> aktivity. A <xref:System.Activities.Statements.Catch%601> typu **TException** obsahuje <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> a <xref:System.Activities.Statements.Catch%601.Action%2A>. Společně se používají k implementaci typické chybové výjimky na základě mechanismu pro zpracování. A <xref:System.Activities.Statements.TryCatch> aktivity spuštění se pokusí jeho <xref:System.Activities.Statements.TryCatch.Try%2A> aktivity. Pokud <xref:System.Activities.Statements.TryCatch.Try%2A> aktivita vyvolá jakoukoliv výjimku, <xref:System.Activities.Statements.TryCatch> aktivita používá jeho **Catch < TException\>**  kolekce tak, aby odpovídaly výjimku. Pokud není nalezena shoda, pak bude <xref:System.Activities.Statements.Catch%601.Action%2A> k odpovídající položce **Catch\<TException >** provádí, slouží jako logiku pro výjimku zpracování chyb. Pokud aktivity v <xref:System.Activities.Statements.TryCatch.Try%2A> části úspěšně dokončena nebo aktivity v rámci <xref:System.Activities.Statements.TryCatch.Catches%2A> úspěšně dokončené <xref:System.Activities.Statements.TryCatch> aktivity spustí jeho <xref:System.Activities.Statements.TryCatch.Finally%2A> aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Výjimky](http://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).  
  
### <a name="using-the-trycatch-activity-designer"></a>Pomocí návrháře aktivity TryCatch  
 **TryCatch** návrháře aktivit najdete v **zpracování chyb** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů** karty na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo řadič + ALT + X.)  
  
 **TryCatch** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface všude, kde aktivity jsou obvykle umístěny, například jako uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří <xref:System.Activities.Statements.TryCatch> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> z TryCatch. <xref:System.Activities.Activity.DisplayName%2A> Hodnota se dá upravit v záhlaví **TryCatch** Návrhář aktivity nebo **DisplayName** pole mřížku vlastností. Další vlastnosti nutné upravit na povrchu **TryCatch** návrháře aktivit.  
  
 Klikněte na tlačítko pro rozbalení v pravém horním rohu **TryCatch** návrháře zobrazíte **zkuste**, **zachytí**, a **nakonec** polích v Rozšířené zobrazení. Chcete-li přidat bloku catch, klikněte na tlačítko **přidat novou aktivitu catch** tlačítko **TryCatch** návrháře. Tlačítko se změní na typ pole se seznamem. Vyberte typ výjimky a stisknutím klávesy ENTER přidejte catch. Po přidání **Catch**, oblast catch se rozšíří a aktivitu můžete přetáhnout do catch k definování logiky provádění pro catch. Všimněte si, že je na pravé straně rozbaleného catch oblasti textového pole. Můžete pojmenovat proměnnou výjimek pomocí tohoto textového pole. Výjimka proměnnou jde použít jenom pro aktivity v rámci stejného **Catch**.  
  
 **TryCatch** návrhář nepodporuje úpravy **Catch**. Pokud chcete změnit typ výjimky, je třeba odstranit **Catch** a přidat nový. A **Catch** je možné odstranit tak, že ji vyberete a jeho odstraněním nebo s použitím **odstranit** nabídky v místní nabídce přistupovat kliknutím pravým tlačítkem.  
  
### <a name="the-trycatch-properties"></a>Vlastnosti TryCatch  
 Následující tabulka ukazuje <xref:System.Activities.Statements.TryCatch>vlastnosti a popisuje, jak se používají v návrháři.  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Určuje volitelný popisný název <xref:System.Activities.Statements.TryCatch> aktivity. Výchozí hodnota je TryCatch.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Aktivita nejdřív nespustí, kdy <xref:System.Activities.Statements.TryCatch> spustí.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Kolekce **Catch** prvků, které mají být vráceny při <xref:System.Activities.Statements.TryCatch.Try%2A> aktivita vyvolá výjimku.<br /><br /> Přidáte třeba alespoň jedné aktivity v <xref:System.Activities.Statements.TryCatch.Catches%2A> nebo aktivity v <xref:System.Activities.Statements.TryCatch.Finally%2A> bloku.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Aktivity, který se spustí při <xref:System.Activities.Statements.TryCatch.Try%2A> a všechny potřebné aktivity ve službě <xref:System.Activities.Statements.TryCatch.Catches%2A> kolekce dokončení provádění.<br /><br /> Přidáte třeba alespoň jedné aktivity v <xref:System.Activities.Statements.TryCatch.Catches%2A> nebo aktivity v <xref:System.Activities.Statements.TryCatch.Finally%2A> bloku.|  
  
## <a name="see-also"></a>Viz také  
 [Kolekce](../workflow-designer/collection-activity-designers.md)   
 [Znovu vyvolejte](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)