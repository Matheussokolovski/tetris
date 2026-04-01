# tetris




import 'package:flutter/material.dart';

class MyWidget extends StatefulWidget {
  const MyWidget({super.key});

  @override
  State<MyWidget> createState() => _MyWidgetState();
}

class _MyWidgetState extends State<MyWidget> {
  // Controllers separados
  TextEditingController _nomeController = TextEditingController();
  TextEditingController _cpfController = TextEditingController();
  TextEditingController _numeroController = TextEditingController();

  @override
  void dispose() {
    _nomeController.dispose();
    _cpfController.dispose();
    _numeroController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.lightBlueAccent,
        foregroundColor: Colors.white,
        centerTitle: true,
        title: const Text('Tela de Prova'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: [
            TextField(
              controller: _nomeController,
              decoration: const InputDecoration(
                labelText: "Nome do Cliente",
                border: OutlineInputBorder(),
              ),
            ),

            SizedBox(height: 16),

            TextField(
              controller: _cpfController,
              keyboardType: TextInputType.number,
              decoration: const InputDecoration(
                labelText: "CPF",
                border: OutlineInputBorder(),
              ),
            ),

            SizedBox(height: 16),

            TextField(
              controller: _numeroController,
              keyboardType: TextInputType.number,
              decoration: const InputDecoration(
                labelText: "Número",
                border: OutlineInputBorder(),
              ),
            ),

            SizedBox(height: 20),

            ElevatedButton(
              onPressed: () {
                String nome = _nomeController.text;
                String cpf = _cpfController.text;
                String numero = _numeroController.text;

                print("Nome: $nome");
                print("CPF: $cpf");
                print("Número: $numero");
              },
              child: const Text("Salvar"),
            ),
          ],
        ),
      ),
    );
  }
}
