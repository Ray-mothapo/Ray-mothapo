var showContent by remember { mutableStateOf(false) }
    var petImageId by remember { mutableStateOf(R.drawable.pet_image) }
    var health by remember { mutableStateOf(0) }
    var hunger by remember { mutableStateOf(0) }
    var cleanliness by remember { mutableStateOf(0) }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        if (!showContent) {
            Text(
                text = "Welcome",
                fontSize = 30.sp,
                fontWeight = FontWeight.Bold
            )
        }

        val petImage: Painter = painterResource(petImageId)

        Image(
            painter = petImage,
            contentDescription = "Pet Image",
            modifier = Modifier
                .size(200.dp)
                .clip(shape = CircleShape)
        )

        Spacer(modifier = Modifier.padding(16.dp))

        if (showContent) {
            Column(
                horizontalAlignment = Alignment.CenterHorizontally
            ) {
                Button(onClick = {
                    petImageId = R.drawable.hunger
                    hunger += 20
                    if (hunger > 100) hunger = 100
                }) {
                    Text(text = "Feed")
                }
                Box(
                    modifier = Modifier
                        .size(75.dp)
                        .background(color = Color.Magenta)
                ) {
                    Text(
                        text = "$hunger%",
                        modifier = Modifier.align(Alignment.Center)
                    )
                }
                Spacer(modifier = Modifier.height(16.dp))

                Column {
                    Button(onClick = {
                        petImageId = R.drawable.cleanliness
                        cleanliness += 20
                        if (cleanliness > 100) cleanliness = 100
                    }) {
                        Text(text = "Cleaning")
                    }
                    Box(
                        modifier = Modifier
                            .size(75.dp)
                            .background(color = Color.Magenta)
                    ) {
                        Text(
                            text = "$cleanliness%",
                            modifier = Modifier.align(Alignment.Center)
                        )
                    }
                }
                Spacer(modifier = Modifier.height(16.dp))

                Button(onClick = {
                    petImageId = R.drawable.health
                    health += 20
                    if (health > 100) health = 100
                }) {
                    Text(text = "Playing")
                }
                Box(
                    modifier = Modifier
                        .size(75.dp)
                        .background(color = Color.Magenta)
                ) {
                    Text(
                        text = "$health%",
                        modifier = Modifier.align(Alignment.Center)
                    )
                }
            }
        } else {
            Button(
                onClick = { showContent = true },
                modifier = Modifier.padding(horizontal = 16.dp)
            ) {
                Text(text = "GO")
            }
        }
    }

}
