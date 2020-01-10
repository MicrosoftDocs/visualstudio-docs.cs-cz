---
title: Chyby a upozornění pro úpravy a pokračováníC#() | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.csharp.enc.error_4001
- vs.csharp.enc.error_4034
- vs.csharp.enc.error_4003
- vs.csharp.enc.error_4026
- vs.csharp.enc.error_4032
- vs.csharp.enc.error_4017
- vs.csharp.enc.error_4053
- vs.csharp.enc.error_4024
- vs.csharp.enc.error_4012
- vs.csharp.enc.error_4066
- vs.csharp.enc.error_4020
- vs.csharp.enc.error_4008
- vs.csharp.enc.error_4033
- vs.csharp.enc.error_4014
- vs.csharp.enc.error_4023
- vs.csharp.enc.error_4011
- vs.csharp.enc.error_4006
- vs.csharp.enc.error_4059
- vs.csharp.enc.error_4015
- vs.csharp.enc.error_4018
- vs.csharp.enc.error_4028
- vs.csharp.enc.error_4013
- vs.csharp.enc.error_4009
- vs.csharp.enc.error_4021
- vs.csharp.enc.error_4065
- vs.csharp.enc.error_4029
- vs.csharp.enc.error_4058
- vs.csharp.enc.error_4019
- vs.csharp.enc.error_4007
- vs.csharp.enc.error_4052
- vs.csharp.enc.error_4025
- vs.csharp.enc.error_4055
- vs.csharp.enc.error_4022
- vs.csharp.enc.error_4002
- vs.csharp.enc.error_4016
- vs.csharp.enc.error_4043
- vs.csharp.enc.error_4027
- vs.csharp.enc.error_4054
- vs.csharp.enc.error_4004
- vs.csharp.enc.error_4010
- vs.csharp.enc.error_4030
- vs.csharp.enc.error_4005
- vs.csharp.enc.error_4035
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], errors and warnings
- errors [C#], debugging
- errors [debugger], Edit and Continue
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eec40bc584e831f8b43b79c9bc7cee5a48a291aa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850975"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>Chyby a upozornění operace Upravit a pokračovat (C#)
Provedli jste úpravy oddílu kódu, který není povolený pro vizuální C# úpravu a pokračování.  
  
 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] upravit a pokračovat umožňuje zastavit provádění programu v režimu pozastavení, provádět změny ve spuštěném kódu a potom pokračovat v provádění programu s nově začleněnými změnami.  
  
 Deklarativní úpravy kódu, které mají vliv na veřejnou strukturu třídy, jsou obecně zakázané a některé úpravy, které lze provést v metodě, tělo vlastnosti nebo soukromé deklarace v rámci třídy, nejsou povoleny. Kdykoli je to možné, kód pro úpravu a pokračování značky, který se nedá upravovat jako světle šedý, a zobrazí chybovou zprávu.  
  
 Další informace o podporovaných úpravách v části Upravit a pokračovat pro [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]najdete v tématu [podporované změnyC#kódu ()](../debugger/supported-code-changes-csharp.md). Pokud potřebujete další informace o konkrétní chybě nebo upozornění, můžete vyhledávat nebo publikovat na [fóru MSDN Visual C# IDE](https://social.msdn.microsoft.com/Forums/en-US/csharpide/threads).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. V nabídce **ladění** vyberte možnost **zpět** a vraťte změny zpět.  
  
     -nebo-  
  
2. Zastavte ladicí relaci, proveďte úpravy a spusťte novou relaci ladění.  
  
## <a name="see-also"></a>Viz také  
 [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
