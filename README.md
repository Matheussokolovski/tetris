# tetris




import 'package:flutter/material.dart';

class MyWidget extends StatefulWidget { const MyWidget({super.key});

@override State createState() => _MyWidgetState(); }

class _MyWidgetState extends State { final _formKey = GlobalKey();

TextEditingController _nomeController = TextEditingController(); TextEditingController _emailController = TextEditingController(); TextEditingController _senhaController = c
String nomeSalvo = ""; String emailSalvo = ""; String senhaSalva = ""; @override void dispose() { _nomeController.dispose(); _emailController.dispose(); _senhaController.dispose(); super.dispose(); }

void cadastrar() { if (_formKey.currentState!.validate()) { setState(() { nomeSalvo = _nomeController.text; emailSalvo = _emailController.text; senhaSalva = _senhaController.text; });

  ScaffoldMessenger.of(context).showSnackBar(
    const SnackBar(content: Text("Cadastro realizado com sucesso!")),
  );
}
}

@override Widget build(BuildContext context) { return Scaffold( appBar: AppBar( title: const Text("Cadastro de Usuário"), backgroundColor: Colors.lightBlueAccent, foregroundColor: Colors.white, centerTitle: true, ), body: Padding( padding: const EdgeInsets.all(16.0), child: Form( key: _formKey, child: Column( children: [ // NOME TextFormField( controller: _nomeController, decoration: const InputDecoration( labelText: "Nome", border: OutlineInputBorder(), ), validator: (value) { if (value == null || value.isEmpty) { return "Digite seu nome"; } return null; }, ),

          const SizedBox(height: 16),

          
          TextFormField(
            controller: _emailController,
            decoration: const InputDecoration(
              labelText: "Email",
              border: OutlineInputBorder(),
            ),
          ),

          const SizedBox(height: 16),

         
          TextFormField(
            controller: _senhaController,
            obscureText: true,
            decoration: const InputDecoration(
              labelText: "Senha",
              border: OutlineInputBorder(),
            ),
          ),

          const SizedBox(height: 20),

          ElevatedButton(
            onPressed: cadastrar,
            style: ElevatedButton.styleFrom(
              minimumSize: const Size(double.infinity, 50),
            ),
            child: const Text("Cadastrar"),
          ),
          const SizedBox(height: 20),
          if (nomeSalvo.isNotEmpty) ...[
            Text("Nome: $nomeSalvo"),
            Text("Email: $emailSalvo"),
            Text("Senha: $senhaSalva"),
          ],
        ],
      ),
    ),
  ),
);
} }
} }
