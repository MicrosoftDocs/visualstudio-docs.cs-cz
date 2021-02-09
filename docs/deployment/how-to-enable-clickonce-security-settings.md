---
title: Povolit nastavení zabezpečení ClickOnce | Microsoft Docs
description: Přečtěte si, jak Průvodce publikováním automaticky povoluje zabezpečení přístupu kódu pro aplikace ClickOnce pro publikování aplikace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 758aecc4f2bf280fd7ff5ca7ca482ee6a3e3d68d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900637"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Postupy: povolení nastavení zabezpečení ClickOnce
Aby bylo možné aplikaci publikovat, je nutné povolit zabezpečení přístupu ke kódu pro aplikace ClickOnce. To se provádí automaticky při publikování aplikace pomocí Průvodce publikováním.

 V některých případech může mít povolení zabezpečení přístupu kódu vliv na výkon při sestavování nebo ladění vaší aplikace; v těchto případech můžete chtít nastavení zabezpečení dočasně zakázat.

 Nastavení zabezpečení ClickOnce lze povolit nebo zakázat na stránce **zabezpečení** **Návrháře projektu**.

### <a name="to-enable-clickonce-security-settings"></a>Povolení nastavení zabezpečení ClickOnce

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **Zabezpečení**.

3. Zaškrtněte políčko **Povolit nastavení zabezpečení ClickOnce** .

     Nastavení zabezpečení aplikace teď můžete přizpůsobit na stránce zabezpečení.

    > [!NOTE]
    > Toto zaškrtávací políčko se automaticky vybere při každém publikování aplikace pomocí průvodce **publikováním** .

### <a name="to-disable-clickonce-security-settings"></a>Zakázání nastavení zabezpečení ClickOnce

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **Zabezpečení**.

3. Zrušte zaškrtnutí políčka **Povolit nastavení zabezpečení ClickOnce** .

     Vaše aplikace se spustí s úplným nastavením zabezpečení důvěryhodnosti. všechna nastavení na stránce **zabezpečení** budou ignorována.

    > [!NOTE]
    > Pokaždé, když je aplikace publikována pomocí Průvodce publikováním, bude toto zaškrtávací políčko zaškrtnuto. po každém úspěšném publikování je nutné ho vymazat znovu.

## <a name="see-also"></a>Viz také
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
