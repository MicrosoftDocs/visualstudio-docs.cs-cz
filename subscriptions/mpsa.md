---
title: Visual Studio odběry na produkty společnosti Microsoft a smlouvou o poskytování služeb (MPSA) | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: Get-Started-Article
description: Visual Studio odběry na produkty společnosti Microsoft a smlouvou o poskytování služeb (MPSA)
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a18565a97c0cd85ce42109961592a57c490d92a1
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2018
ms.locfileid: "30864499"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Visual Studio odběry ve Products společnosti Microsoft a služby smlouvy (MPSA)

Pokud jste zakoupili předplatné Visual Studio prostřednictvím programu MPSA, měli vědět, než můžete stát správce předplatných s Visual Studio a přiřadit odběry uživatelům několik věci. Pokud jste již byla nastavili jako správce, pak můžete přejít přímo na odběry v sadě Visual Studio [portálu pro správu](https://manage.visualstudio.com/). 

Jako odběratele MPSA jste se seznámili na portál, kde můžete spravovat vaše prostředky zakoupené prostřednictvím MPSA. Tento nový portál je volána [centra Business](https://businessaccount.microsoft.com/), který podporuje některé stejné a nové funkce, stejně jako na svazek licencování Service Center (VLSC). Patří sem zobrazení vaší licenční souhrn, objednávky, soubory ke stažení, klíče, uživatelé, atd. Však chovají Visual Studio odběry ve MPSA mnohem jako cloudové služby. Centra Business také využívá pracovních účtů se přihlásit, nikoli Microsoft Accounts. Pokud vaše organizace používá cloudové služby, jako je Office 365 nebo Azure Active Directory a e-mailu je součástí každého z těchto dvou služeb je již pracovní účet. To vám umožní zaregistrovat do centra Business si stávající heslo, které vaše organizace určeny pro vás. Pokud vaše organizace nepoužívá cloudové služby a e-mailu není pracovní účet na všech, Nedělejte si starosti jako smíte ji použít k registraci do centra Business.

Kromě toho odběry v sadě Visual Studio [portálu pro správu](https://manage.visualstudio.com/) je, kde předplatná se přiřadí odběratele po stát správce sady Visual Studio. V MPSA musí být zřízená odběry Visual Studio na jeho odpovídající management portal, což je Visual Studio odběry portálu pro správu. K tomu, budete muset přidružení účtu nákupu klienta (tj. contoso.onmicrosoft.com). 

Upozorňujeme, že existují dva typy klientů (spravovaného klienta a nespravovaného tenanta). Spravovaného klienta odkazuje na klienta, které je již spravován jako správci v rámci organizace. 

Nespravovaného tenanta je klient bez jakékoli správcům a již není použitelné pro Online služeb, například Office 365. Nespravované klientů jsou také vytvořen při registraci k centru obchodní s e-mailu, který není pracovní účet. Pokud se zobrazí dotaz, vytvořit heslo při registraci do centra Business, pak to znamená, že e-mailu nebyla pracovní účet a je vytvořen nespravovaného tenanta.

Před dokončením přidružení klienta jsou zde několik požadavky nebo kroky potřebné k Visual Studio odběry správce.

## <a name="pre-tenant-association-managed-tenant"></a>Předem klienta přidružení (spravovaného klienta)
-   Musí být registrovaný uživatel k centru firmy.
-   Uživatel správce (minimálně) nebo globální správce musí být v rámci klienta, které jsou součástí. (To platí, pokud vaše společnost už používá cloudové služby). Buď role je potřeba se za správce předplatných Visual Studio.
-   Musí být globální správce v klientovi, které jsou součástí moct přidružit účtu nákupu pro vašeho klienta.
-   Musí být účtu správce nebo správce účtu centra Business.
-   "Zemi nebo oblasti" pole v rámci profilu uživatele (a ostatní uživatele) v [Azure](https://portal.azure.com/) musí být naplněny odpovídajícím způsobem v závislosti na vaší oblasti (tj. USA, certifikační Autority, atd.). 

> [!NOTE]
> Jako stačí splňují kritéria v kroku 2 a 5, nejsou všechny uživatele, kterým chcete, aby správci odběry Visual Studio nemusí být uživatelé v Centru pro firmy.

Jakmile jste splnili kritéria v předchozích 5 krocích můžete přidružit účtu nákupu pro vašeho klienta následujících kroků.
1.  Přihlaste se k [centra Business](https://businessaccount.microsoft.com/).
2.  Klikněte na **účet** a klikněte na příkaz **přidružit domény**.
3.  Vyberte vaše **nákupu účet** (Pokud máte více než jeden).
4.  Vyberte vaše **klienta** (tj. contoso.onmicrosoft.com).
5.  Klikněte na tlačítko **přidružte doménu**.

Při přidružení budou všichni uživatelé, které splňují kritéria pro potřeby zřídit jako Visual Studio odběry správci minut obvykle. Ale v některých případech může trvat až 24 hodin. Po zřízení nebudete mít přístup k portálu správy předplatných Visual Studio. Pokud to trvá déle než 24 hodin, obraťte se na podporu MPSA.

> [!NOTE]
> Pokud jsou noví uživatelé, kteří mají splnění kritérií pro kroky 2 a 5 (po přidružení) obraťte se na podporu MPSA. Podpora MPSA bude pomoc ke zřízení noví správci odběry Visual Studio.

## <a name="tenant-association-unmanaged"></a>Přidružení klienta (nespravovaný)

Pokud jste zaregistrovali k centru obchodní s e-mailu, který nebyl pracovní účet (není zaregistrovaná ve službě Azure Active Directory "Azure AD"), jak je vysvětleno v odstavci pět výše uvedené, se jemně liší přidružení klienta. Musíte provést, co se nazývá "převzetí domény". Během tohoto procesu budete vytvářet sami globální správce, který změní vašeho klienta z nespravovaných do spravovaných.

Podrobnější vysvětlení pro tento proces, můžete použít [rychlý Start provede](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Stáhněte si prosím v příručce s názvem *"Instalace a použití vaše Online služby"* který vás provede převzetí domény. Až to uděláte účtu nákup bude také přidružen ke klientovi.

> [!NOTE]
> Po dokončení procesu převzetí domény, je nutné splnit kritéria z pěti kroků v části pro předběžné klienta přidružení (spravované). Po splnění těchto kritérií, pouze je nutné se obrátit na podporu MPSA zřídit další správce předplatných Visual Studio.

Pokud jste vyžadovat pomoc nebo máte nějaké dotazy se můžete obrátit na podporu přes telefon nebo e-mail.

Podpora MPSA: **1-866-200-9611**, k dispozici pondělí – pátek 5:30:00 do 5:30 PM Tichomoří

E-mailu: ngvlsup@microsoft.com
