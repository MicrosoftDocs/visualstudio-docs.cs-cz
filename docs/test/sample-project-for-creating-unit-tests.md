---
title: Ukázkový kód pro vytváření testů jednotek
description: Tento článek obsahuje ukázkový kód, který lze testovat pomocí testování částí v sadě Visual Studio.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: deddf46a479e0ab8d4e0bebbaf3fffe4d90b622d
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51293444"
---
# <a name="sample-code-for-testing"></a>Ukázkový kód pro testování

Tento vzorový kód obsahuje třídu, *BankAccount*, pomocí různých metod, které můžete otestovat pomocí testů jednotek.

Kód se používá v následujících návodech:

- [Vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Tento názorný postup vás provede kroky k vytvoření a přizpůsobení testů jednotek, je spustit a podívejte se na výsledky testu.
- [Použijte nástroj příkazového řádku test](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). V tomto názorném postupu použijete *MSTest.exe* příkazový řádek pro spuštění testů a zobrazení výsledků.

## <a name="sample-code"></a>Ukázkový kód

Pouze touto úmyslnou chybou v této ukázce je, že v metoda debetní "m_balance += částka" by měla mít minus není plus podepsat před znaménko rovná se.

```csharp
using System;

namespace BankAccountNS
{
    /// <summary>
    /// Bank Account demo class.
    /// </summary>
    public class BankAccount
    {
        private string m_customerName;

        private double m_balance;

        private bool m_frozen = false;

        private BankAccount()
        {
        }

        public BankAccount(string customerName, double balance)
        {
            m_customerName = customerName;
            m_balance = balance;
        }

        public string CustomerName
        {
            get { return m_customerName; }
        }

        public double Balance
        {
            get { return m_balance; }
        }

        public void Debit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount > m_balance)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount; // intentionally incorrect code
        }

        public void Credit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount;
        }

        private void FreezeAccount()
        {
            m_frozen = true;
        }

        private void UnfreezeAccount()
        {
            m_frozen = false;
        }

        public static void Main()
        {
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

            ba.Credit(5.77);
            ba.Debit(11.22);
            Console.WriteLine("Current balance is ${0}", ba.Balance);
        }
    }
}
```

/ * Vzorové společnosti, organizace, produkty, názvy domén, e-mailové adresy, loga, osoby, místa a události použité v ukázkách jsou smyšlené. Žádné jejich spojení se skutečnou společností, organizaci, produktu, název domény, e-mailovou adresu, loga, osoby, místa nebo události je určena ji vyvozovat. \*/

## <a name="create-the-project"></a>Vytvoření projektu

Pro práci s tímto kódem, nejprve vytvořte projekt pro něj v aplikaci Visual Studio. Postupujte podle kroků pro vytvoření projektu v [návod: vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test).

## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření a spuštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Návod: Použití nástroje příkazového řádku test](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
