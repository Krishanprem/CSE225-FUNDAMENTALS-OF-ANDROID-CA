package com.example.firstca225

import android.os.Bundle
import android.widget.Toast
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.background
import androidx.compose.foundation.clickable
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.lazy.*
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.filled.ExitToApp
import androidx.compose.material.icons.filled.Person
import androidx.compose.material.icons.filled.Settings
import androidx.compose.material3.*
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.platform.LocalContext
import androidx.compose.ui.unit.dp

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            DashboardScreen()
        }
    }
}

@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun DashboardScreen() {

    val context = LocalContext.current

    val topics = listOf(
        "Android", "Kotlin", "DSA", "Web", "AI",
        "ML", "Cloud", "DevOps", "Python", "Java"
    )

    val courses = List(20) {
        Course(
            "Course $it",
            "Description of course $it",
            if (it % 2 == 0) "New" else "In Progress"
        )
    }

    Scaffold(
        topBar = {
            TopAppBar(
                colors = TopAppBarDefaults.topAppBarColors(
                    containerColor = Color(0xFF6200EE),
                    titleContentColor = Color.White
                ),
                title = { Text("Dashboard") },
                actions = {

                    IconButton(onClick = {
                        Toast.makeText(context, "Profile Clicked", Toast.LENGTH_SHORT).show()
                    }) {
                        Icon(Icons.Default.Person, contentDescription = "", tint = Color.White)
                    }

                    IconButton(onClick = {
                        Toast.makeText(context, "Settings Clicked", Toast.LENGTH_SHORT).show()
                    }) {
                        Icon(Icons.Default.Settings, contentDescription = "", tint = Color.White)
                    }

                    IconButton(onClick = {
                        Toast.makeText(context, "Logout Clicked", Toast.LENGTH_SHORT).show()
                    }) {
                        Icon(Icons.Default.ExitToApp, contentDescription = "", tint = Color.White)
                    }
                }
            )
        }
    ) { padding ->

        LazyColumn(
            modifier = Modifier
                .padding(padding)
                .background(Color(0xFFF5F5F5))
        ) {

            item {
                Spacer(modifier = Modifier.height(10.dp))

                LazyRow(
                    contentPadding = PaddingValues(horizontal = 10.dp)
                ) {
                    items(topics) { topic ->
                        ChipItem(topic)
                    }
                }

                Spacer(modifier = Modifier.height(10.dp))
            }
            items(courses) { course ->
                CourseCard(course)
            }
        }
    }
}


@Composable
fun ChipItem(text: String) {

    val chipColor = when (text) {
        "Android" -> Color(0xFF4CAF50)
        "Kotlin" -> Color(0xFFFF9800)
        "DSA" -> Color(0xFF2196F3)
        "Web" -> Color(0xFFE91E63)
        else -> Color(0xFF9C27B0)
    }

    Box(
        modifier = Modifier
            .padding(end = 8.dp)
            .background(chipColor, shape = RoundedCornerShape(20.dp))
            .clickable { }
            .padding(horizontal = 16.dp, vertical = 8.dp)
    ) {
        Text(text = text, color = Color.White)
    }
}


data class Course(
    val title: String,
    val desc: String,
    val status: String
)


@Composable
fun CourseCard(course: Course) {

    val (bgColor, statusColor) = if (course.status == "New") {
        Pair(Color(0xFFE8F5E9), Color(0xFF2E7D32))   // Green theme
    } else {
        Pair(Color(0xFFE3F2FD), Color(0xFF1565C0))   // Blue theme
    }

    Card(
        shape = RoundedCornerShape(18.dp),
        elevation = CardDefaults.cardElevation(10.dp),
        colors = CardDefaults.cardColors(containerColor = bgColor),
        modifier = Modifier
            .fillMaxWidth()
            .padding(horizontal = 12.dp, vertical = 8.dp)
    ) {
        Column(modifier = Modifier.padding(16.dp)) {

            Text(
                text = course.title,
                style = MaterialTheme.typography.titleMedium,
                color = Color.Black
            )

            Spacer(modifier = Modifier.height(6.dp))

            Text(
                text = course.desc,
                color = Color.DarkGray
            )

            Spacer(modifier = Modifier.height(10.dp))

            Box(
                modifier = Modifier
                    .background(
                        color = statusColor.copy(alpha = 0.15f),
                        shape = RoundedCornerShape(10.dp)
                    )
                    .padding(horizontal = 10.dp, vertical = 4.dp)
            ) {
                Text(
                    text = course.status,
                    color = statusColor
                )
            }
        }
    }
}
