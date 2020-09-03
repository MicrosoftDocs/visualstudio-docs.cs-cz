---
title: Připojovací řetězec obsahuje přihlašovací údaje s nešifrovaným textovým heslem a nepoužívá integrované zabezpečení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8fc2a428753e9650bb0dfebdb2bfdfdde10697a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672289"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Připojovací řetězec obsahuje přihlašovací údaje s heslem uloženým jako nešifrovaný text a nevyužívá integrované zabezpečení.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete uložit připojovací řetězec do aktuálního souboru DBML a konfiguračních souborů aplikace s těmito citlivými informacemi?  Kliknutím na ne uložte připojovací řetězec bez citlivých informací.

 Při práci s datovými připojeními, která obsahují citlivé informace (hesla, která jsou obsažena v připojovacím řetězci), máte možnost Uložit připojovací řetězec do souboru DBML a konfiguračního souboru aplikace v projektu s nebo bez citlivých informací.

> [!WARNING]
> Explicitním nastavením vlastnosti **připojení** vlastnost **nastavení aplikace** na **hodnotu NEPRAVDA** přidá heslo do souboru DBML.

### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Uložení připojovacího řetězce s citlivými informacemi v nastavení aplikace projektu

- Klikněte na **Ano**.

     Připojovací řetězec je uložen jako nastavení aplikace. Připojovací řetězec obsahuje citlivé informace v prostém textu. Soubor DBML neobsahuje citlivé informace.

### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Uložení připojovacího řetězce bez citlivých informací v nastavení aplikace projektu

- Klikněte na tlačítko **ne**.

     Připojovací řetězec je uložen jako nastavení aplikace, ale heslo není zahrnuto.

## <a name="see-also"></a>Viz také
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
