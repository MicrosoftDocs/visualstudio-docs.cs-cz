---
title: Ověření nastavení vlastnosti služby IIS | Microsoft Docs
description: Naučte se ověřit nastavení vlastností IIS, která jste nastavili pro webovou aplikaci pomocí nástroje pro správu služby IIS.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ed11efb0d493844456d2493153a41df140095cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853115"
---
# <a name="how-to-verify-iis-property-settings"></a>Postupy: Ověření nastavení vlastnosti služby IIS

Můžete nastavit vlastnosti webové aplikace pomocí nástroje pro správu služby IIS. Tyto vlastnosti musí být správně nastaveny, aby bylo možné aplikaci spustit, takže ověřování těchto nastavení je často nezbytným krokem při řešení potíží.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Postup kontroly nastavení služby IIS pro webovou aplikaci

1. Otevřete okno **Nástroje pro správu** : v nabídce **Start** přejděte na **programy** a potom klikněte na **Nástroje pro správu**. Pokud se **Nástroje pro správu** nezobrazí v nabídce **programy** , pak je vyhledejte v **Ovládacích panelech**.

   - V systému Windows 2000 vyberte možnost **Správce služeb Internetu**.

   - V systému Windows XP vyberte možnost **Internetová informační služba**.

   - V systému Windows Server 2003 poklikejte na **Správa serveru**.

        Otevře se okno **Správa serveru** . V části **aplikační server** klikněte na **Spravovat tento aplikační server**.

        Otevře se okno **aplikační server** . V levém podokně otevřete uzel **správce Internetová informační služba (IIS)** .

2. V dialogovém okně klikněte na uzel ovládacího prvku strom pro váš počítač. Klikněte na uzel **webové servery** a vyberte uzel webové aplikace. Bude se jednat buď o uzel webu, a tedy na stejné úrovni **jako výchozí** uzel webu nebo na uzlu virtuálního adresáře pod existujícím uzlem webu.

3. Klikněte pravým tlačítkem myši na webovou aplikaci a v místní nabídce klikněte na **vlastnosti**.

4. Ověřte nastavení zabezpečení webové aplikace:

   1. V okně **vlastnosti** webové aplikace klikněte na kartu **zabezpečení adresáře** a pak klikněte na **Upravit**.

   2. V dialogovém okně **metody ověřování** vyberte možnost **Povolit anonymní přístup** a **integrované ověřování systému Windows** , pokud již nejsou vybrány.

   3. Kliknutím na tlačítko **OK** zavřete dialogové okno **metody ověřování** .

5. V případě serverové aplikace ATL ověřte, zda je příkaz LADIT přidružen k vašemu rozšíření ISAPI. Další informace naleznete v tématu [How to: přidružte příkaz ladění s příponou](/previous-versions/ms165022(v=vs.100)).

6. V případě [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace se ujistěte, že virtuální složka aplikace má název aplikace nastavený ve **Správci Internetová informační služba (IIS)** **Správce služeb Internetu** nebo **Internetová informační služba**.

   1. V okně **vlastnosti** webové aplikace vyberte kartu **adresář** , pokud je aplikace ve virtuálním adresáři nebo na kartě **domovského adresáře** , pokud je aplikace na webu.

   2. Ověřte, že název v **místní cestě** odpovídá názvu adresáře, ve kterém byla aplikace skutečně nasazena.

   3. V části **nastavení aplikace** zadejte název kořenového adresáře, který obsahuje aplikaci.

   4. Kliknutím na tlačítko **OK** zavřete dialogové okno **vlastnosti** .

7. V případě [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace klikněte na kartu **ASP.NET** a ověřte, zda je zadána správná verze systému [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

8. Kliknutím na tlačítko **OK** zavřete dialogové okno **vlastnosti** .

9. Kliknutím na tlačítko **OK** zavřete dialogové okno **Internetová informační služba (Správce služby IIS)**, **Správce služeb Internetu** nebo **Internetová informační služba** .

## <a name="see-also"></a>Viz také

- [Řešení potíží](../debugger/debugging-web-applications-troubleshooting.md)