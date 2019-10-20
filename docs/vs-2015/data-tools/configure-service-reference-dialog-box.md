---
title: Dialogové okno Konfigurace odkazu na službu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651117"
---
# <a name="configure-service-reference-dialog-box"></a>Dialogové okno Nastavit odkaz na službu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dialogové okno **Konfigurovat odkaz na službu** umožňuje konfigurovat chování služby [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] Services.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Chcete-li získat přístup k dialogovému oknu **Konfigurovat odkaz** na službu, klikněte pravým tlačítkem myši na odkaz na službu v **Průzkumník řešení** a vyberte možnost **Konfigurovat odkaz na službu**. K dialogovému oknu se dostanete také tak, že kliknete na tlačítko **Upřesnit** v **dialogovém okně Přidat odkaz na službu**.

## <a name="task-list"></a>Seznam úkolů

- Chcete-li změnit adresu, kde je hostována služba WCF, zadejte novou adresu do pole **adresa** .

- Chcete-li změnit úroveň přístupu pro třídy v klientovi WCF, vyberte klíčové slovo na úrovni přístupu v seznamu **vygenerované třídy na úrovni přístupu** .

- Chcete-li volat metody služby WCF asynchronně, zaškrtněte políčko **Generovat asynchronní operace** .

- Chcete-li generovat typy kontraktů zpráv v klientovi WCF, zaškrtněte políčko **vždy generovat kontrakty zprávy** .

- Chcete-li určit typy kolekce seznamu nebo slovníku pro klienta WCF, vyberte typy ze seznamu **typ kolekce** a **typ kolekce slovníku** .

- Chcete-li zakázat sdílení typů, zrušte zaškrtnutí políčka **znovu použít typy v odkazovaných sestaveních** . Pokud chcete povolit sdílení typů pro podmnožinu odkazovaných sestavení, zaškrtněte políčko **znovu použít typy v odkazovaných sestaveních** , vyberte možnost **znovu použít typy v zadaných odkazovaných sestaveních**a vyberte požadované odkazy v **odkazovaném sestavení. seznam sestavení**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Adresa** Slouží k aktualizaci webové adresy, kde odkaz na službu vyhledává službu. Například během vývoje může být služba hostována na vývojovém serveru a později přesunuta na provozní server, který vyžaduje změnu adresy.

> [!NOTE]
> Element Address není k dispozici, když se v dialogovém okně **Přidat odkaz na službu**zobrazuje dialogové okno **Konfigurovat odkaz na službu** .

 **Úroveň přístupu pro vygenerované třídy** Určuje úroveň přístupu kódu pro klientské třídy WCF.

> [!NOTE]
> Pro projekty webu je tato možnost vždy nastavená na `Public` a nelze ji změnit. Další informace najdete v tématu [řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md).

 **Generovat asynchronní operace** Určuje, zda budou metody služby WCF volány synchronně (výchozí) nebo asynchronně.

 **Generování operací založených na úlohách** Při psaní asynchronního kódu Tato možnost umožňuje využít výhod aplikace Task Parallel Library (TPL), která byla představena s rozhraním .NET 4. Viz [Task Parallel Library (TPL)](https://msdn.microsoft.com/library/dd460717.aspx).

 **Vždy generovat kontrakty zpráv** Určuje, zda budou generovány typy kontraktů zpráv pro klienta WCF. Další informace o kontraktech zpráv najdete v tématu [Použití kontraktů zpráv](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).

 **Typ kolekce** Určuje typ kolekce seznamu pro klienta WCF. Výchozí typ je <xref:System.Array>.

 **Typ kolekce slovníku** Určuje typ kolekce Dictionary pro klienta WCF. Výchozí typ je <xref:System.Collections.Generic.Dictionary%602>.

 **Znovu použít typy v odkazovaných sestaveních** Určuje, zda se klient služby WCF pokusí znovu použít, který již existuje v odkazovaných sestaveních, namísto generování nových typů při přidání nebo aktualizaci služby. Ve výchozím nastavení je tato možnost zaškrtnutá.

 **Znovu použít typy ve všech odkazovaných sestaveních** Je-li toto políčko zaškrtnuto, budou použity všechny typy v **odkazovaných sestaveních seznamu** , pokud je to možné. Ve výchozím nastavení je tato možnost vybraná.

 **Znovu použít typy v zadaných odkazovaných sestaveních** Pokud je tato možnost vybrána, budou znovu použity pouze vybrané typy v **odkazovaných sestaveních seznamu** .

 **Seznam odkazovaných sestavení** Obsahuje seznam odkazovaných sestavení pro projekt nebo Web. Když je vybrána možnost **znovu použít typy v zadaných odkazovaných sestaveních** , je možné vybrat nebo vymazat jednotlivá sestavení.

 **Přidat webový odkaz** Zobrazí [dialogové okno NIB: Přidat webový odkaz](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).

> [!NOTE]
> Tato možnost by měla být použita pouze pro projekty, které cílí na verzi 2,0 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

> [!NOTE]
> Tlačítko **Přidat webový odkaz** je dostupné pouze v případě, že se dialogové okno **Konfigurovat odkaz na službu** zobrazí v **dialogovém okně Přidat odkaz na službu**.

## <a name="see-also"></a>Viz také
 [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9) [Postupy: Přidání odkazu na webovou službu](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation Services a WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
