---
title: Předplatná sady Visual Studio ve smlouvě o produktech a službách společnosti Microsoft (MPSA)| Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/03/2020
ms.topic: conceptual
description: Předplatná sady Visual Studio ve smlouvě o produktech a službách společnosti Microsoft (MPSA)
ms.openlocfilehash: e59929404febda5a07ba13f7dc230ab89e09addf
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232206"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Předplatná sady Visual Studio ve smlouvě o produktech a službách společnosti Microsoft (MPSA)
Pokud jste si zakoupili předplatná sady Visual Studio prostřednictvím programu MPSA, je třeba si uvědomit několik věcí, než se můžete stát správcem předplatných sady Visual Studio a přiřadit předplatná uživatelům. Pokud jste již byli nastaveni jako správce, můžete přejít přímo na [portál pro správu](https://manage.visualstudio.com/)předplatných sady Visual Studio .

Zákazníci mpsa nyní spravují majetek zakoupený prostřednictvím mpsa na novém portálu s názvem [Business Center](https://businessaccount.microsoft.com/Customer), který podporuje funkce podobné Centru multilicenčních služeb (VLSC). Patří mezi ně zobrazení souhrnu licencí, objednávky, soubory ke stažení, klíče, uživatelé atd. Předplatná Visual Studia v mpsa však chovají podobně jako cloudové služby. Business Center také používá pracovní účty k přihlášení, nikoli účty Microsoft (MSA). Pokud vaše organizace používá cloudové služby, jako je Office 365 nebo Azure Active Directory, a váš e-mail je součástí jedné z těchto dvou služeb, je to už pracovní účet. To vám umožní zaregistrovat se do Business Center pomocí stávajícího hesla. Pokud vaše organizace cloudové služby nepoužívá a váš e-mail není pracovní účet, můžete ho použít k registraci do Business Centra.

Kromě toho portál pro [správu](https://manage.visualstudio.com/) předplatných sady Visual Studio je místo, kde odběry budou přiřazeny předplatitelům, jakmile se stanete správcem předplatných sady Visual Studio. V MPSA, Visual Studio předplatná musí být zřízena na jejich příslušný portál pro správu, což je portál pro správu předplatných Visual Studio. Chcete-li to provést, musíte přidružit svůj nákupní účet ke klientovi (tj. contoso.onmicrosoft.com).

Vezměte prosím na vědomí, že existují dva typy klientů - spravované klienty a nespravované klienty. Spravovaný klient odkazuje na klienta, který je již spravován správci v rámci organizace.

Nespravovaný klient je tenant bez přiřazených správců a není použitelný pro online služby, jako je Office 365. Nespravovaní klienti se také vytvářejí při registraci do Business Center pomocí e-mailu, který není pracovním účtem. Pokud jste byli při registraci do Business Centra požádáni o vytvoření hesla, znamená to, že váš e-mail nebyl pracovním účtem a vytvořil nespravovaného klienta.

Tady je několik požadavků/kroků potřebných k tomu, aby se stal správcem předplatných Visual Studio před dokončením přidružení klienta.

## <a name="pre-tenant-association-managed-tenant"></a>Přidružení před tenantem (spravovaný tenant)
- Musíte být registrovaným uživatelem Business Center.
- Musíte být správce uživatele (minimálně) nebo globální správce v rámci tenanta, který jste součástí. (To platí, pokud vaše společnost již cloudové služby používá). Buď role je potřeba být správce předplatných sady Visual Studio.
- Abyste mohli přidružit svůj nákupní účet ke svému tenantovi, musíte být globálním správcem v tenantovi, jehož jste součástí.
- V Business Centru musíte být správcem účtu nebo správcem účtu.
- Pole "Země nebo oblast" v rámci vašeho uživatelského profilu (a všech ostatních uživatelů) v [Azure](https://portal.azure.com/) musí být vhodně vyplněno v závislosti na vaší oblasti (tj. USA, certifikační autorita atd.). 

> [!NOTE]
> Všichni uživatelé, které chcete vytvořit správce předplatných sady Visual Studio, nemusí být uživateli v Business Center, protože potřebují pouze splňovat kritéria 2 a 5.

Jakmile splníte výše uvedená kritéria, můžete přistoupit k přidružení nákupního účtu ke svému tenantovi podle následujících kroků.
1. Přihlaste se do [Business Center](https://businessaccount.microsoft.com/Customer).
2. Klikněte na kartu **Účet** a zvolte **Přidružené domény**.
3. Vyberte svůj **nákupní účet** (pokud máte více než jeden).
4. Vyberte **svého klienta** (tj. contoso.onmicrosoft.com).
5. Klepněte na **položku Přidružená doména**.

Po přidružení budou všichni uživatelé, kteří splňují kritéria, obvykle zřídit jako správci předplatných sady Visual Studio během několika minut. Někdy však může trvat až 24 hodin. Po zřízení vašeho tenanta budete mít přístup k portálu pro správu předplatných visual studia. Pokud to trvá déle než 24 hodin, obraťte se na podporu mpsa pomocí těchto kroků:
1. Připojit khttps://www.microsoft.com/licensing/mpsa/default
2. V horní části stránky klikněte na nabídku **Další.** 
3. Zvolte **podporu**
4. Zvolte **Podporu licencování**
5. Vyberte možnost podpory, která nejlépe vyhovuje vašim potřebám. 

> [!NOTE]
> Pokud existují noví uživatelé, kteří splňují kritéria v krocích 2 a 5 (po přidružení), musíte kontaktovat podporu MPSA. Podpora MPSA bude poskytovat pomoc při zřizování nových správců předplatných sady Visual Studio.

## <a name="tenant-association-unmanaged"></a>Přidružení klienta (nespravované)
Pokud jste se zaregistrovali do Business Center s e-mailem, který nebyl pracovní účet (není registrován ve službě Azure Active Directory "Azure AD"), jak je vysvětleno výše, bude přidružení klienta mírně odlišné. Budete muset provést to, co se nazývá "převzetí domény". Během tohoto procesu se stanete globálním správcem, který změní vašeho klienta z nespravovaného na spravovaného.

Podrobnější vysvětlení tohoto procesu získáte pomocí [úvodních příruček](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Stáhněte si prosím průvodce s názvem *"Nastavení a používání online služeb",* který vás provede převzetím domény. Po dokončení bude váš nákupní účet také přidružen k vašemu tenantovi.

> [!NOTE]
> Po dokončení procesu převzetí domény je nutné dodržovat kritéria z pěti kroků v části Pro přidružení před tenantem (Spravované). Jakmile jsou splněna kritéria, bude nutné kontaktovat pouze podporu MPSA a zřídit další správce předplatných sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úpravy předplatných](edit-license.md)
- [Odstranění předplatných](delete-license.md)
- [Určení maximálního využití](maximum-usage.md)
