---
title: Dialogové okno Nastavit odkaz na službu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f0cb2737356813a9b637d7f16e9d5cda704c022a
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389497"
---
# <a name="configure-service-reference-dialog-box"></a>Nastavit odkaz na službu – dialogové okno

**Nastavit odkaz na službu** dialogové okno umožňuje konfigurovat chování služby Windows Communication Foundation (WCF).

Pro přístup **nastavit odkaz na službu** dialogové okno, klikněte pravým tlačítkem na službu odkazovat v **Průzkumníku řešení** a zvolte **nastavit odkaz na službu**. Dialogové okno se můžete dostat taky kliknutím **Upřesnit** tlačítko **Add Service Reference Dialog Box**.

## <a name="task-list"></a>Seznam úkolů

- Chcete-li změnit adresu, kde se hostuje službu WCF, zadejte novou adresu ve **adresu** pole.

- Chcete-li změnit úroveň přístupu pro třídy v klienta WCF, vyberte v klíčové slovo úroveň přístupu **přístup k úrovni pro vygenerované třídy** seznamu.

- Asynchronně volat metodu služby WCF, vyberte **Generovat asynchronní operace** zaškrtávací políčko.

- Chcete-li generovat typy kontraktů zpráv v klienta WCF, vyberte **vždy generovat kontrakty zprávy** zaškrtávací políčko.

- Typy kolekcí seznamu nebo slovníku pro klienta WCF, vyberte typy z **typ kolekce** a **kolekce typu Dictionary** seznamy.

- Chcete-li zakázat sdílení typů, zrušte **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko. Chcete-li povolit typ sdílení pro podmnožinu odkazovaná sestavení, vyberte **znovu použít typy v odkazovaných sestaveních** zaškrtněte políčko **znovu použít typy v zadaných odkazovaných sestaveních**a vyberte požadovaný odkazy v **seznam sestavení odkazovaných**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

 **Adresa**

 Aktualizuje webovou adresu, kde bude vypadat odkaz na službu pro službu. Například během vývoje, služba může být hostovaný na vývojovém serveru a později přesunout na produkční server vyžadující změnu adresy.

> [!NOTE]
> Address element není k dispozici při **nastavit odkaz na službu** zobrazí dialogové okno z **Add Service Reference Dialog Box**.

 **Úroveň přístupu pro vygenerované třídy**

 Určuje úroveň přístupu kód třídy klientů WCF.

> [!NOTE]
> Pro projekty webových stránek, tato možnost je vždycky nastavený na `Public` a nedá se změnit. Další informace najdete v tématu [řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md).

 **Generovat asynchronní operace**

 Určuje, zda je WCF service metody volat synchronně (výchozí) nebo asynchronně.

 **Generování operací podle úloh**

 Při psaní asynchronního kódu, tato možnost vám umožní využít z Task Parallel Library (TPL), které se zavedly s .NET 4. Zobrazit [úkolů Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Vždy generovat kontrakty zprávy**

 Určuje, zda jsou typy kontraktů zpráv generování klienta WCF. Další informace o kontraktů zpráv najdete v tématu [použití kontraktů zpráv](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Typ kolekce**

 Určuje typ kolekce seznamu pro klienta WCF. Výchozí typ je <xref:System.Array>.

 **Kolekce typu Dictionary**

 Určuje typ kolekce slovníku pro klienta WCF. Výchozí typ je <xref:System.Collections.Generic.Dictionary%602>.

 **Znovu použít typy v odkazovaných sestaveních**

 Určuje, zda klienta WCF se pokusí znovu použít, co již existuje v odkazovaných sestaveních, místo aby generovala nových typů, když se služba přidá nebo aktualizuje. Ve výchozím nastavení je tato možnost zaškrtnutá.

 **Znovu použít typy ve všech odkazovaných sestaveních**

 Pokud je vybráno, všechny typy v **seznam sestavení odkazovaných** údaje znovu použijí Pokud je to možné. Ve výchozím nastavení je tato možnost vybrána.

 **Znovu použít typy v zadaných odkazovaných sestaveních**

 Pokud je vybráno, pouze vybrané typy v **seznam sestavení odkazovaných** údaje znovu použijí.

 **Seznam odkazovaných sestavení**

 Obsahuje seznam odkazovaných sestavení pro projekt nebo webu. Když vyberete **znovu použít typy v zadaných odkazovaných sestaveních**, můžete zaškrtněte nebo zrušte zaškrtnutí jednotlivá sestavení.

 **Přidat webový odkaz**

 Zobrazí **přidat webový odkaz** dialogové okno.

> [!NOTE]
> Tato možnost by měl používat pouze pro projekty, které cílí na verzi 2.0 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].
>
> [!NOTE]
> **Přidat webový odkaz** tlačítko je k dispozici pouze při **nastavit odkaz na službu** zobrazí dialogové okno z **Add Service Reference Dialog Box**.

## <a name="see-also"></a>Viz také:

- [Postupy: Přidání odkazu na webovou službu](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/configure-service-reference-dialog-box.md)