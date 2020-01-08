---
title: Návrhář aktivity Návrhář postupu provádění – TryCatch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b70f1d3174990ec12c621dff4a45ce4d899ceb4e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593067"
---
# <a name="trycatch-activity-designer"></a>Návrhář aktivity TryCatch

Návrhář aktivity **TryCatch** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.TryCatch>.

## <a name="the-trycatch-activity"></a>Aktivita TryCatch
 Aktivita <xref:System.Activities.Statements.TryCatch> obsahuje aktivitu <xref:System.Activities.Statements.TryCatch.Try%2A>, kolekci **Catch\<TException >** a aktivitu <xref:System.Activities.Statements.TryCatch.Finally%2A>. <xref:System.Activities.Statements.Catch%601> typu **TException** obsahuje <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> a <xref:System.Activities.Statements.Catch%601.Action%2A>. Společně se používají k implementaci typického mechanismu zpracování chyb na základě výjimek. Aktivita <xref:System.Activities.Statements.TryCatch> se pokusí spustit aktivitu <xref:System.Activities.Statements.TryCatch.Try%2A>. Pokud aktivita <xref:System.Activities.Statements.TryCatch.Try%2A> vyvolá jakoukoli výjimku, <xref:System.Activities.Statements.TryCatch> aktivita použije její kolekci **Catch < TException\>** ke spárování s výjimkou. Pokud existuje shoda, pak se spustí <xref:System.Activities.Statements.Catch%601.Action%2A> odpovídající **> Catch\<TException** , který slouží jako logika zpracování chyb pro výjimku. Pokud se aktivity v oddílu <xref:System.Activities.Statements.TryCatch.Try%2A> úspěšně dokončí nebo se aktivity v <xref:System.Activities.Statements.TryCatch.Catches%2A> úspěšně dokončí, <xref:System.Activities.Statements.TryCatch> aktivita spustí svou <xref:System.Activities.Statements.TryCatch.Finally%2A> aktivitu. Další informace najdete v tématu [výjimky pracovního postupu Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Pomocí návrháře aktivity TryCatch

Přístup k Návrháři aktivity **TryCatch** v kategorii **zpracování chyb** sady **nástrojů**.

Návrhář aktivity **TryCatch** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.TryCatch> s výchozím <xref:System.Activities.Activity.DisplayName%2A> TryCatch. Hodnotu <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivity **TryCatch** nebo v poli **DisplayName** v mřížce vlastností. Ostatní vlastnosti musí být upraveny na povrchu návrháře aktivity **TryCatch** .

Kliknutím na tlačítko Rozbalit v pravém horním rohu návrháře **TryCatch** se v rozbaleném zobrazení zobrazí pole **Try**, **catch**a **finally** . Pokud chcete přidat catch, klikněte na tlačítko **Přidat nové catch** v **TryCatch** designeru. Tlačítko se změní na pole se seznamem typu. Vyberte typ výjimky a stisknutím klávesy ENTER přidejte catch. Po přidání **catch**se oblast catch rozbalí a aktivita může být vyřazena do catch pro definování logiky spuštění pro catch. Všimněte si, že na pravé straně rozbalené oblasti catch je textové pole. Proměnnou výjimky můžete pojmenovat pomocí tohoto textového pole. Proměnnou výjimky lze použít pouze pro aktivity v rámci stejného **catch**.

Návrhář **TryCatch** nepodporuje úpravy **catch**. Pokud chcete změnit typ výjimky, je nutné odstranit **catch** a přidat nový. **Catch** se dá odstranit tak, že ho vyberete a odstraníte, nebo výběrem možnosti **Odstranit** v kontextové nabídce, ke které se přistupovalo kliknutím pravým tlačítkem.

### <a name="the-trycatch-properties"></a>Vlastnosti TryCatch

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.TryCatch>a popisuje, jak se používají v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Určuje nepovinný popisný název aktivity <xref:System.Activities.Statements.TryCatch>. Výchozí hodnota je TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Nepravda|Aktivita se poprvé spustí při spuštění <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Nepravda|Kolekce elementů **catch** , které mají být zkontrolovány, pokud aktivita <xref:System.Activities.Statements.TryCatch.Try%2A> vyvolá výjimku.<br /><br /> Potřebujete alespoň přidat jednu aktivitu do <xref:System.Activities.Statements.TryCatch.Catches%2A> nebo aktivitu v bloku <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Nepravda|Aktivita, která se má provést, když <xref:System.Activities.Statements.TryCatch.Try%2A> a všechny potřebné aktivity v kolekci <xref:System.Activities.Statements.TryCatch.Catches%2A> dokončí provádění.<br /><br /> Potřebujete alespoň přidat jednu aktivitu do <xref:System.Activities.Statements.TryCatch.Catches%2A> nebo aktivitu v bloku <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Viz také:

- [Kolekce](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
