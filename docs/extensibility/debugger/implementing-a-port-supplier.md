---
title: Implementace dodavatele portu | Microsoft Docs
description: Seznamte se s implementací dodavatele portu, který je nezbytný při ladění na počítač, který není typu DCOM, nebo když nové zařízení vyžaduje podporu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98cc83ac9640241f0f97dc6e4adaacf8f90599b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059909"
---
# <a name="implement-a-port-supplier"></a>Implementace dodavatele portu
Dodavatel portu dodává porty na žádost do Správce ladění relace (SDM). Dodavatel portu se musí implementovat při ladění na počítač, který není typu DCOM, nebo když nové zařízení vyžaduje podporu. Chcete-li například poskytnout ladění na mobilní telefon, můžete nastavit dodavatele portu, který poskytuje porty, které se připojují k mobilnímu telefonu (například pomocí INFRAČERVENého připojení nebo připojení k buňce) a vyčísluje procesy a programy běžící na telefonu.

 Pro ladění programů na počítačích se systémem Windows (včetně vzdáleného ladění) poskytuje Visual Studio dodavatelům portů pro nativní procesy a procesy modulu CLR (Common Language Runtime), takže v těchto případech není nutné nastavovat vlastního dodavatele portu.

## <a name="in-this-section"></a>V této části
 [Implementace a registrace dodavatele portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Popisuje, jak model SDM komunikuje s dodavatelem portu a jeho porty.

 [Požadovaná rozhraní dodavatele portu](../../extensibility/debugger/required-port-supplier-interfaces.md) Dokumentuje rozhraní, která je nutné implementovat pro získání dodavatele portu.

## <a name="related-sections"></a>Související oddíly
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní koncepty architektury ladění.

## <a name="see-also"></a>Viz také
 [Rozšiřitelnost ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
