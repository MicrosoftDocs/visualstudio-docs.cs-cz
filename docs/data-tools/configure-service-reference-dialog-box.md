---
title: Dialogové okno Nastavit odkaz na službu
description: Pomocí dialogového okna Konfigurovat odkaz na službu v aplikaci Visual Studio můžete konfigurovat chování služby Windows Communication Foundation (WCF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1dc1d82b0267e5e0655f3ebef8eb08806ad319a8
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518723"
---
# <a name="configure-service-reference-dialog-box"></a>Nastavit odkaz na službu – dialogové okno

Dialogové okno **Konfigurovat odkaz na službu** umožňuje konfigurovat chování služby Windows Communication Foundation (WCF).

Chcete-li získat přístup k dialogovému oknu **Konfigurovat odkaz** na službu, klikněte pravým tlačítkem myši na odkaz na službu v **Průzkumník řešení** a vyberte možnost **Konfigurovat odkaz na službu**. K dialogovému oknu se dostanete také tak, že kliknete na tlačítko **Upřesnit** v **dialogovém okně Přidat odkaz na službu**.

## <a name="task-list"></a>Seznam úkolů

- Chcete-li změnit adresu, kde je hostována služba WCF, zadejte novou adresu do pole **adresa** .

- Chcete-li změnit úroveň přístupu pro třídy v klientovi WCF, vyberte klíčové slovo na úrovni přístupu v seznamu **vygenerované třídy na úrovni přístupu** .

- Chcete-li volat metody služby WCF asynchronně, zaškrtněte políčko **Generovat asynchronní operace** .

- Chcete-li generovat typy kontraktů zpráv v klientovi WCF, zaškrtněte políčko **vždy generovat kontrakty zprávy** .

- Chcete-li určit typy kolekce seznamu nebo slovníku pro klienta WCF, vyberte typy ze seznamu **typ kolekce** a **typ kolekce slovníku** .

- Chcete-li zakázat sdílení typů, zrušte zaškrtnutí políčka **znovu použít typy v odkazovaných sestaveních** . Pokud chcete povolit sdílení typů pro podmnožinu odkazovaných sestavení, zaškrtněte políčko **znovu použít typy v odkazovaných sestaveních** , vyberte možnost **znovu použít typy v zadaných odkazovaných sestaveních** a vyberte požadované odkazy v **seznamu odkazovaných sestavení**.

## <a name="uielement-list"></a>UIElement – seznam

**Adresa**

Aktualizuje webovou adresu, kde odkaz na službu vyhledává službu. Například během vývoje může být služba hostována na vývojovém serveru a později přesunuta na provozní server, což vyžaduje změnu adresy.

> [!NOTE]
> Element Address není k dispozici, když se v dialogovém okně **Přidat odkaz na službu** zobrazuje dialogové okno **Konfigurovat odkaz na službu** .

**Úroveň přístupu pro vygenerované třídy**

Určuje úroveň přístupu kódu pro klientské třídy WCF.

> [!NOTE]
> Pro projekty webu je tato možnost vždy nastavena na `Public` a nelze ji změnit. Další informace najdete v tématu [řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md).

**Generovat asynchronní operace**

Určuje, zda jsou metody služby WCF volány synchronně (výchozí) nebo asynchronně.

**Generování operací založených na úlohách**

Při psaní asynchronního kódu umožňuje tato možnost využít výhod úlohy Parallel Library (TPL), která byla představena s rozhraním .NET 4. Viz [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

**Vždy generovat kontrakty zpráv**

Určuje, zda jsou generovány typy kontraktů zpráv pro klienta WCF. Další informace o kontraktech zpráv najdete v tématu [Použití kontraktů zpráv](/dotnet/framework/wcf/feature-details/using-message-contracts).

**Typ kolekce**

Určuje typ kolekce seznamu pro klienta WCF. Výchozí typ je <xref:System.Array> .

**Typ kolekce slovníku**

Určuje typ kolekce Dictionary pro klienta WCF. Výchozí typ je <xref:System.Collections.Generic.Dictionary%602> .

**Znovu použít typy v odkazovaných sestaveních**

Určuje, zda se klient služby WCF pokusí znovu použít to, co již existuje v odkazovaných sestaveních, namísto generování nových typů při přidání nebo aktualizaci služby. Ve výchozím nastavení je tato možnost zaškrtnutá.

**Znovu použít typy ve všech odkazovaných sestaveních**

Je-li toto políčko zaškrtnuto, budou použity všechny typy v **odkazovaných sestaveních seznamu** , pokud je to možné. Tato možnost je vybrána ve výchozím nastavení.

**Znovu použít typy v zadaných odkazovaných sestaveních**

Když je toto políčko zaškrtnuté, znovu se použijí jenom vybrané typy v **odkazovaných sestaveních seznamu** .

**Seznam odkazovaných sestavení**

Obsahuje seznam odkazovaných sestavení pro projekt nebo Web. Když vyberete možnost **znovu použít typy v zadaných odkazovaných sestaveních** , můžete vybrat nebo vymazat jednotlivá sestavení.

**Přidat webový odkaz**

Zobrazí dialogové okno **Přidat webový odkaz** .

> [!NOTE]
> Tato možnost by měla být použita pouze pro projekty, které cílí na verzi 2,0 .NET Framework.
>
> [!NOTE]
> Tlačítko **Přidat webový odkaz** je dostupné jenom v případě, že se v **dialogovém okně Přidat odkaz na službu** zobrazuje dialogové okno **Konfigurovat odkaz na službu** .

## <a name="see-also"></a>Viz také:

- [Postupy: Přidání odkazu na webovou službu](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Služby Windows Communication Foundation a služby WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
