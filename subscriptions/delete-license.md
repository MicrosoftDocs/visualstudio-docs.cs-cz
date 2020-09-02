---
title: Odstranit přiřazení předplatného na portálu pro správu předplatných sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 06/16/2020
ms.topic: how-to
description: Zjistěte, jak můžou správci odstraňovat přiřazení předplatného.
ms.openlocfilehash: 4f952f574132afbd405c82c75fcddfc952bffb48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87434270"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Odstranit přiřazení v předplatných sady Visual Studio
Pokud již předplatitel nevyžaduje předplatné sady Visual Studio, například když odejdou ze společnosti, dokončí projekt nebo přepne na novou roli úlohy, můžete odebrat jejich předplatné a přiřadit ho někomu jinému. Upozorňujeme, že při opětovném přiřazení předplatného dojde k resetování všech výhod předplatitele.  Nový uživatel bude moci vyžádat všechny neoprávněné klíče a zobrazit dříve požadované klíče, ale omezení deklarací identity nebudou **resetována** .  Pro organizace, které mají smlouvy Enterprise (EA), se všechny výhody, které použil původní uživatel, jako je třeba školení Pluralsight, resetují. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Odstraní přiřazení předplatného.
1. Klikněte na jméno předplatitele, kterého chcete odebrat. Chcete-li vybrat více odběratelů k odebrání, můžete kliknout na kroužek vlevo od názvu předplatitele a vybrat si ho.  Případně můžete podržet klávesu **CTRL** a kliknout na každého předplatitele, kterého chcete odebrat. Chcete-li odebrat řadu předplatitelů, klikněte na první, stiskněte klávesu **SHIFT** a klikněte na poslední z nich.  Stisknutím **kombinace kláves CTRL + a** vyberte a odeberte všechny předplatitele. 
2. Pokud chcete vybrané odběratele odstranit, klikněte na **Odstranit**.
3. Jakmile se zobrazí zpráva s výzvou k potvrzení odstranění, klikněte na tlačítko **OK**.
   > [!div class="mx-imgBorder"]
   > ![Odstranit předplatitele](_img/delete-license/delete-subscribers.png "Vyberte uživatele, které chcete odstranit, a klikněte na Odstranit. Pomocí kláves CTRL a Shift můžete vybrat více odběratelů.")

   > [!NOTE]
   > Hromadné odstranění pomocí šablony není k dispozici. Organizace, které spravují přiřazení předplatného prostřednictvím skupin zabezpečení Azure Active Directory, najdete v [našem článku](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) , kde najdete další informace o tom, jak dochází k odstranění.  

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Potřebujete změnit předplatné, aniž byste ho odstranili?  Informace o tom, jak [Upravit odběry](edit-license.md)
- Nápovědu k vyhledání konkrétního předplatného najdete v tématu [hledání předplatného](search-license.md).
- Potřebujete vytvořit seznam všech vašich předplatných?  Podívejte se prosím na [Export předplatných](exporting-subscriptions.md).


