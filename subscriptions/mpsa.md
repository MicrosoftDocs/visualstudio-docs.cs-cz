---
title: Předplatná sady Visual Studio v MPSA | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 09/03/2020
ms.topic: conceptual
description: Přečtěte si o správě předplatných sady Visual Studio v rámci smlouvy o produktech a službách společnosti Microsoft (MPSA).
ms.openlocfilehash: 388c847ce19ca7136efb7757fbc87bffdc35a673
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903803"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Předplatná sady Visual Studio v rámci smlouvy o produktech a službách společnosti Microsoft (MPSA)
Pokud jste si zakoupili předplatná sady Visual Studio prostřednictvím programu MPSA, měli byste si být vědomi, že před tím, než se stanete správcem předplatných sady Visual Studio a přiřadíte odběry uživatelům. Pokud jste již nastavili jako správce, můžete přejít přímo na [portál pro správu](https://manage.visualstudio.com/)předplatných sady Visual Studio.

Zákazníci MPSA spravují prostředky zakoupené prostřednictvím MPSA na portálu s názvem [Business Center](https://businessaccount.microsoft.com/Customer), který podporuje funkce podobně jako na webu Volume Licensing Service Center (VLSC). Patří mezi ně zobrazení souhrnu licencí, objednávek, souborů ke stažení, klíčů, uživatelů atd. Předplatná sady Visual Studio v MPSA se však chovají podobně jako Cloud Services. Centrum Business Center také používá pracovní účty k přihlašování místo účtů Microsoft (MSA). Pokud vaše organizace používá cloudové služby, jako je například Office 365 nebo Azure Active Directory, a váš e-mail je součástí některé z těchto dvou služeb, již je to pracovní účet. To vám umožní zaregistrovat se do centra pro firmy s vaším stávajícím heslem. Pokud vaše organizace nepoužívá cloudové služby a váš e-mail není pracovní účet, můžete ho použít k registraci do obchodního centra.

Kromě toho [portál pro správu](https://manage.visualstudio.com/) předplatných sady Visual Studio přiřadíte odběry, jakmile se stanete správcem předplatných sady Visual Studio. V MPSA musí být předplatná sady Visual Studio zřízena na příslušný portál pro správu, což je portál pro správu předplatných sady Visual Studio. K tomu je potřeba přidružit svůj nákupní účet ke klientovi (tj. contoso.onmicrosoft.com).

Upozorňujeme, že existují dva typy klientů spravovaných klienty a nespravované klienty. Spravovaný tenant odkazuje na tenanta, který už spravuje správci v rámci organizace.

Nespravovaný tenant je tenant bez přiřazených správců a není použitelný pro online služby, jako je například Office 365. Nespravované klienty se vytvoří taky při registraci do centra Business Center pomocí e-mailu, který není pracovním účtem. Pokud jste byli požádáni o vytvoření hesla při registraci do obchodního centra, znamená to, že váš e-mail nebyl pracovní účet a vytvořil nespravovaného tenanta.

Tady je několik požadavků/kroků, které se stanou správcem předplatných sady Visual Studio před dokončením přidružení tenanta.

## <a name="pre-tenant-association-managed-tenant"></a>Přidružení před tenantovi (spravovaný tenant)
- Musíte být registrovaným uživatelem služby Business Center.
- Musíte být správcem uživatelů (minimálně) nebo globálním správcem v rámci tenanta, kterého jste členem. (To platí, pokud vaše společnost už používá Cloud Services). Kterákoli z rolí musí být správce předplatných sady Visual Studio.
- Abyste mohli k vašemu tenantovi přidružit svůj nákupní účet, musíte být globálním správcem v tenantovi, který jste členem.
- Musíte být správcem účtu nebo správcem účtů v centru podnikání.
- Pole země nebo oblast v rámci vašeho uživatelského profilu (a jakýkoli jiný uživatel) v [Azure](https://portal.azure.com/) se musí správně naplnit v závislosti na vaší oblasti (například USA, CA atd.). 

> [!NOTE]
> Všichni uživatelé, u kterých chcete, aby správci předplatných sady Visual Studio nemuseli být uživateli v obchodním centru, protože potřebují splňovat kritéria 2 a 5.

Jakmile splníte kritéria výše, můžete k vašemu tenantovi přidružit svůj nákupní účet podle následujících kroků.
1. Přihlaste se do [centra Business Center](https://businessaccount.microsoft.com/Customer).
2. Klikněte na kartu **účet** a vyberte **přidružit domény** .
3. Vyberte svůj **Nákupní účet** (Pokud máte víc než jeden).
4. Vyberte svého **tenanta** (například contoso.onmicrosoft.com).
5. Klikněte na **přidružit doménu** .

Při přidružení budou všichni uživatelé, kteří splňují kritéria, obvykle zřizovat během několika minut jako správci předplatných sady Visual Studio. V časech ale může trvat až 24 hodin. Po zřízení tenanta budete mít přístup k portálu pro správu předplatných sady Visual Studio. Pokud bude trvat déle než 24 hodin, kontaktujte prosím podporu MPSA pomocí těchto kroků:
1. Připojit k <https://www.microsoft.com/licensing/mpsa/default>
2. Klikněte na nabídku **Další** v horní části stránky. 
3. Zvolit **podporu**
4. Zvolit **podporu licencování**
5. Vyberte možnost podpory, která nejlépe vyhovuje vašim potřebám. 

> [!NOTE]
> Pokud existují noví uživatelé, kteří splňují kritéria v krocích 2 a 5 (po přidružení), musíte se obrátit na podporu MPSA. Podpora MPSA vám poskytne pomoc při zřizování nových správců předplatných sady Visual Studio.

## <a name="tenant-association-unmanaged"></a>Přidružení tenanta (nespravované)
Pokud jste se zaregistrovali do centra Business Center pomocí e-mailu, který nebyl pracovním účtem (není zaregistrován v Azure Active Directory "Azure AD"), jak je vysvětleno výše, přidružení tenanta se mírně liší. Budete muset provést akci, která se nazývá "převzetí služeb při selhání domény". Během tohoto procesu sami provedete globálního správce, který změní vašeho tenanta z nespravovaného na spravované.

Pro podrobnější vysvětlení tohoto procesu můžete použít [průvodce rychlé zprovoznění](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Stáhněte si prosím příručku s názvem *"Setup" a použijte své online služby* , které vás provedou převzetím domény. Až to dokončíte, Váš nákupní účet se taky přidruží k vašemu tenantovi.

> [!NOTE]
> Po dokončení procesu převzetí domény musíte dodržovat kritéria z pěti kroků v části pro přidružení předběžného tenanta (spravované). Jakmile jsou kritéria splněná, bude nutné, abyste se obrátili na podporu MPSA a zřídili další správce předplatných sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace ke službě Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Odstranění předplatných](delete-license.md)
- [Určení maximálního využití](maximum-usage.md)