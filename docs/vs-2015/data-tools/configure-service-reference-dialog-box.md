---
title: Služba odkaz dialogové okno Konfigurace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24da338378739afca6ad228582a29069aebde9f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266971"
---
# <a name="configure-service-reference-dialog-box"></a>Dialogové okno Nastavit odkaz na službu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
**Nastavit odkaz na službu** dialogové okno umožňuje konfigurovat chování [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] služby.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte nastavení importu a exportu v nabídce Nástroje. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pro přístup **nastavit odkaz na službu** dialogové okno, klikněte pravým tlačítkem na službu odkazovat v **Průzkumníku řešení** a zvolte **nastavit odkaz na službu**. Dialogové okno se můžete dostat taky kliknutím **Upřesnit** tlačítko **Add Service Reference Dialog Box**.  
  
## <a name="task-list"></a>Seznam úloh  
  
-   Chcete-li změnit adresu, kde se hostuje službu WCF, zadejte novou adresu ve **adresu** pole.  
  
-   Chcete-li změnit úroveň přístupu pro třídy v klienta WCF, vyberte v klíčové slovo úroveň přístupu **přístup k úrovni pro vygenerované třídy** seznamu.  
  
-   Asynchronně volat metodu služby WCF, vyberte **Generovat asynchronní operace** zaškrtávací políčko.  
  
-   Chcete-li generovat typy kontraktů zpráv v klienta WCF, vyberte **vždy generovat kontrakty zprávy** zaškrtávací políčko.  
  
-   Typy kolekcí seznamu nebo slovníku pro klienta WCF, vyberte typy z **typ kolekce** a **kolekce typu Dictionary** seznamy.  
  
-   Chcete-li zakázat sdílení typů, zrušte **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko. Chcete-li povolit typ sdílení pro podmnožinu odkazovaná sestavení, vyberte **znovu použít typy v odkazovaných sestaveních** zaškrtněte políčko **znovu použít typy v zadaných odkazovaných sestaveních**a vyberte požadovaný odkazy v **seznam sestavení odkazovaných**.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Adresa**  
 Používá k aktualizaci webovou adresu, kde bude vypadat odkaz na službu pro službu. Například během vývoje služby mohou být hostované na vývojový server pak později přesunout na produkční server vyžadující změnu adresy.  
  
> [!NOTE]
>  Address element není k dispozici při **nastavit odkaz na službu** zobrazí dialogové okno z **Add Service Reference Dialog Box**.  
  
 **Úroveň přístupu pro vygenerované třídy**  
 Určuje úroveň přístupu kód třídy klientů WCF.  
  
> [!NOTE]
>  Pro projekty webových stránek, tato možnost je vždycky nastavený na `Public` a nedá se změnit. Další informace najdete v tématu [řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md).  
  
 **Generovat asynchronní operace**  
 Určuje, zda synchronně bude volat metody služby WCF (výchozí) nebo asynchronně.  
  
 **Generování operací podle úloh**  
 Při psaní asynchronního kódu, tato možnost umožňuje využívat nástroje Task Parallel Library (TPL), které se zavedly s využitím .net 4. Zobrazit [úkolů Parallel Library (TPL)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Vždy generovat kontrakty zprávy**  
 Určuje, zda typy kontraktů zpráv bude vytvořen pro klienta WCF. Další informace o kontraktů zpráv najdete v tématu [použití kontraktů zpráv](http://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).  
  
 **Typ kolekce**  
 Určuje typ kolekce seznamu pro klienta WCF. Výchozí typ je <xref:System.Array>.  
  
 **Kolekce typu Dictionary**  
 Určuje typ kolekce slovníku pro klienta WCF. Výchozí typ je <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Znovu použít typy v odkazovaných sestaveních**  
 Určuje, zda klienta WCF se pokusí znovu použít, které již existují v odkazovaných sestaveních namísto generování nové typy při přidání nebo aktualizaci služby. Ve výchozím nastavení je tato možnost zaškrtnutá.  
  
 **Znovu použít typy ve všech odkazovaných sestaveních**  
 Pokud je vybráno, všechny typy v **seznam sestavení odkazovaných** bude znovu použita Pokud je to možné. Ve výchozím nastavení je tato možnost vybrána.  
  
 **Znovu použít typy v zadaných odkazovaných sestaveních**  
 Pokud je vybráno, pouze vybrané typy v **seznam sestavení odkazovaných** bude znovu použita.  
  
 **Seznam odkazovaných sestavení**  
 Obsahuje seznam odkazovaných sestavení pro projekt nebo webu. Když **znovu použít typy v zadaných odkazovaných sestaveních** je vybrána, jednotlivá sestavení mohou být zaškrtnuto nebo ne.  
  
 **Přidat webový odkaz**  
 Zobrazí [NIB: Přidat webové Reference Dialog Box](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Tato možnost by měla sloužit pouze pro projekty, které cílí na verzi 2.0 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  **Přidat webový odkaz** tlačítko je k dispozici pouze tehdy, když **nastavit odkaz na službu** zobrazí dialogové okno z **Add Service Reference Dialog Box**.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [Postupy: Přidání odkazu na webovou službu](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/configure-service-reference-dialog-box.md)

